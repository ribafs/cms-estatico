# Static CMS

## Crie seu site/blog com o CMS preferido e Hospede no Github

## URL deste projeto

https://github.com/ribafs/static-cms

## Vantagens

- Rápido
- Seguro
- Gratuito

## Desvantagens

Tem desvantagens sim, como tudo nesta vida. Uma forte é não contar com os recursos de sites dinâmicos como bancos de dados, linguagem dinâmica, etc.

## Siga os passos

- Criar um site local com Joomla em /var/www/html/professor
- Criar uma conta no Github 'ribafs' e um repositório 'ribafs.github.io'
- Criar a pasta /home/ribafs/localhost
- Clonar o repositório ribafs.github.io na pasta local /home/ribafs/localhost/professor
cd /home/ribafs/localhost
git clone git@github.com:ribafs/ribafs.github.io.git professor
chown -R ribafs:ribafs /home/ribafs/localhost
touch index.html
echo '<script>location="professor.html"</script>' > index.html

Criar um script na pasta /usr/local/bin chamado cms, contendo:

# Baixar um site completo. Já usei para baixar meu site criado em Joomla e converti para um site estático, que está aqui:
# https://ribamar.net.br
wget \
     --recursive \
     --no-clobber \
     -P /home/ribafs/localhost \
     --page-requisites \
     --html-extension \
     --convert-links \
     --restrict-file-names=windows \
     --no-parent \
http://localhost/professor
cd /home/ribafs/localhost/professor
git add .
git commit -m 'Update'
git pull
git push

sudo chmod +x /usr/local/bin/cms

## Observação

Fique atento, pois caso tenha criado a chave do SSH com senha a mesma será solicitada duas vezes ao final

## Copiar também o último backup de professor para /home/ribafs/github/professor

## Possibilidades:

- Tecla de atalho para terminal executando o script 'cms'
- Ícone do menu com lançador para executar 'cms'

## Testes

Testado apenas em Linux com wget. Me parece que também funciona em Windows ou Mac usando um software como o Httrack.

## Licença

MIT
