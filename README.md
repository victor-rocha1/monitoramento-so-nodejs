# Monitoramento do Sistema Operacional

Script Node.js que monitora e registra as informações do sistema. Abaixo estão os detalhes das funcionalidades deste código:

## Importação de Módulos
- `os`: Módulo do Node.js para interagir com o sistema operacional.
- `fs`: Módulo do Node.js para manipulação do sistema de arquivos.
- `path`: Módulo do Node.js para manipulação de caminhos de arquivos e diretórios.

## Mapeamento de Plataformas
- `systemPlatformMap`: Um objeto que mapeia os identificadores de plataforma do Node.js para nomes de sistemas operacionais legíveis (`win32` para Windows, `linux` para Linux, `darwin` para MacOS e `freebsd` para FreeBSD).

## Função `getSystemInfo`
- Coleta várias informações do sistema, incluindo:
  - Sistema Operacional (`system`).
  - Arquitetura (`arch`).
  - Modelo do Processador (`cpu`).
  - Tempo de atividade do sistema (`uptime`), formatado como `dias:horas:minutos:segundos`.
  - Memória RAM total (`ramTotal`) e usada (`ramUsage`), em gigabytes.
  - Porcentagem de uso da memória RAM (`ramUsagePercent`).
- Retorna essas informações em um objeto.

## Função `printLog`
- Recebe um objeto com as informações do sistema.
- Limpa o console (`console.clear()`).
- Imprime as informações formatadas no console usando `console.log`.

## Função `saveLog`
- Recebe um objeto com as informações do sistema.
- Formata essas informações como uma string (`logContent`).
- Verifica se o diretório `/log` existe. Se não existir, ele cria o diretório (`fs.mkdirSync`).
- Salva o conteúdo formatado em um arquivo `log.txt` dentro do diretório `/log` utilizando `fs.appendFileSync`.

## Monitoramento Contínuo
- Usa `setInterval` para executar as funções `getSystemInfo`, `printLog` e `saveLog` a cada 1000 milissegundos (1 segundo), criando um monitoramento contínuo do sistema.

## Comentários Adicionais
- **Tratamento de Erros**: O código atual não inclui tratamento de erros. Em um cenário de produção, seria importante adicionar verificação de erros, especialmente ao interagir com o sistema de arquivos.
- **Permissões de Escrita**: A escrita no diretório raiz (`/log`) pode exigir permissões de administrador/superusuário, o que pode não ser ideal ou possível em todos os ambientes.
- **Eficácia**: A execução a cada segundo pode ser ajustada conforme a necessidade, pois pode ser muito frequente dependendo do uso pretendido.