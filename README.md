💾 PROJETO DE BACKUP E RESTAURAÇÃO DE BANCO DE DADOS 🗄️

📌 Sobre o Projeto

Este projeto foi desenvolvido como parte do curso técnico da Escola SENAI A. Jacob Lafer (Santo André - SP) pelo aluno Giovanni Allevi.

O objetivo principal é demonstrar na prática os procedimentos essenciais de gerenciamento, segurança e recuperação de banco de dados utilizando o MySQL, contemplando tarefas como:

📤 Exportação e geração de backups completos e parciais via mysqldump

🗑️ Simulação de desastres (exclusão de tabelas e bancos de dados)

📥 Restauração e recuperação de dados perdidos

🔍 Validação da integridade das tabelas após restauração

👨‍💻 Autor

Nome: Giovanni Allevi

Instituição: Escola SENAI A. Jacob Lafer

Localização: Santo André - SP

🛠️ Tecnologias e Ferramentas Utilizadas

🗄️ MySQL Database

💻 Prompt de Comando / Terminal (CMD)

🐬 MySQL Workbench

📄 Arquivos .sql para Dump de Dados

📋 Passo a Passo de Execução

1️⃣ Verificação da Estrutura de Arquivos 📁

Geração dos arquivos de backup no diretório do usuário local (Users\Dev_1o_Ano), garantindo a coexistência dos dumps:

backup.sql (Backup Completo)

eleitor.sql (Backup da Tabela Específica)

2️⃣ Exportação de Backups (Dump) 📤

Execução dos comandos de backup usando o utilitário mysqldump:

Backup completo do Banco de Dados (sistema_eleitoral):

mysqldump -u root -p sistema_eleitoral > backup.sql


Backup apenas da tabela eleitor:

mysqldump -u root -p sistema_eleitoral eleitor > eleitor.sql


3️⃣ Simulação de Falha / Exclusão Parcial 🛑

Simulação da perda de dados acidental removendo especificamente a tabela eleitor:

mysql -u root -p -e "DROP TABLE sistema_eleitoral.eleitor;"


4️⃣ Restauração Parcial 🔄

Restaurando unicamente a tabela eleitor a partir do dump específico previamente criado (eleitor.sql):

mysql -u root -p sistema_eleitoral < eleitor.sql


5️⃣ Confirmação Visual da Restauração Parcial 🎯

Verificação via interface gráfica (MySQL Workbench) confirmando o retorno da tabela eleitor no esquema sistema_eleitoral:

sistema_eleitoral
  └── Tables
      ├── candidatos
      └── eleitor  ✅ (Restaurada com sucesso)


6️⃣ Simulação de Desastre Total (Drop Database) 💥

Simulação da perda completa da base de dados através do comando DROP DATABASE:

mysql -u root -p -e "DROP DATABASE sistema_eleitoral;"


7️⃣ Restauração Completa da Base de Dados 🚀

Restaurando todas as tabelas e dados através do arquivo de backup completo (backup.sql):

mysql -u root -p sistema_eleitoral < backup.sql


8️⃣ Validação Final dos Dados 📊

Checagem do status e lista de tabelas para garantir a integridade de todas as entidades após o processo de restauração completo:

mysql -u root -p -e "USE sistema_eleitoral; SHOW TABLES;"


Resultado:

+----------------------------+
| Tables_in_sistema_eleitoral|
+----------------------------+
| candidatos                 |
| eleitor                    |
+----------------------------+


💡 Importância do Backup no Ambiente Corporativo e Pessoal

"Usar o backup é vital tanto para empresas quanto para uso pessoal. Ele assegura que informações críticas não sejam perdidas permanentemente devido a falhas operacionais, ataques cibernéticos ou comandos executados incorretamente por erro humano. Manter uma rotina e estratégia sólida de cópias de segurança garante a continuidade do negócio e a proteção patrimonial dos dados."
