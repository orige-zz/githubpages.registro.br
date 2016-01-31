# GitHub:Pages no Registro.br #

Este é um pequeno e simples tutorial para a utilização de domínios personalizados  registrados no **registro.br** com **github:pages** para seu projeto ou página pessoal.


## O que é o GitHub:Pages ##

GitHub Pages é um sistema de hospedagem grátis e de fácil uso para algum projeto ou página pessoal com um repositório no GitHub.

É possível criar páginas personalizadas para seus projetos ou utilizar temas oferecidos pelo próprio GitHub. Você pode criar sites estáticos com apenas a força de seus conhecimentos em **HTML** e **CSS** ou até blogs com conteúdos dinâmicos utilizando o **Jekyll**. 

Não vou abordar aqui como criar passo a passo cada tipo de site mas você pode encontrar como [nessa página](https://help.github.com/categories/20/articles).

## Criando o site para o seu projeto ##

Para criar um site para o seu projeto, faça um `clone` dele para sua máquina:   
`$ git clone https://github.com/voce/seu_projeto.git`

Após isso, crie um *branch* orfão com o nome de **gh-pages** e remova todos os arquivos do seu projeto nesse *branch*, utilizando os seguintes comandos:

`$ git checkout --orphan gh-pages`  
`$ git rm -rf .` 

Construa o site do seu projeto nesse *branch*. Um comentário útil é que este *branch* só aparecerá no comando `git branch` após o seu primeiro `commit`.

Dê um `push` desse novo *branch* para o repositório do projeto:   
`$ git push origin gh-pages`

Caso você queira saber como criar seu próprio site ou um site utilizando *Jekyll*, confira a documentação fornecida pelo GitHub.

## Configurando um domínio próprio para o seu projeto no GitHub##

Caso você não queira um domínio personalizado para o site do seu projeto, já é possível acessá-lo pelo link: `https://voce.github.com/site_do_projeto`.

No nosso caso vamos utilizar um domínio próprio para o projeto, registrado no **registro.br**.

Para isso crie um arquivo chamado `CNAME` nesse mesmo branch e coloque dentro dele o nome do domínio personalizado que você desejar. Faça o `commit` e dê outro `push` no repositório:
`$ echo "seuprojeto.com.br" > CNAME`

Ok. Pela parte do GitHub já está tudo pronto. Agora falta apenas as configurações de DNS no **registro.br**.

# No registro.br #

Faça o login no site do [registro.br](http://www.registro.br) e clique no domínio registrado para seu projeto.

1. Marque a opção **Utilizar os servidores do Registro.br**
2. Clique em **Salvar & Editar DNS**
3. 2. Clique em **Modo Avançado**
4. Agora clique em **+Record** para *setar* o DNS do seu projeto no github.

#### Edição de Zona ####

O Github agora disponibiliza dois endereços para seus servidores DNS. É preciso cadastrar os dois para o mesmo domínio.
1. Deixe o campo de **subdomínios** vazio.
2. No campo **Tipo** selecione **A**.
3. No campo **Dados** coloque o seguinte endereço: **192.30.252.153**
4. Clique em **+Record** para abrir um novo cadastro.

Repita a operação cadastrando o segundo ip **192.30.252.153**.

Agora precisamos colocar o subdomínio `www` para funcionar também.

1. No campo subdomínio coloque **www**.
2. No campo **Tipo** escolha **CNAME**
3. No campo **Dados** coloque o endereço utilizado no arquivo `CNAME` de seu projeto: **seuprojeto.com.br**.
4. Clique em **Salvar**.

**Pronto!**

## Observações ##

**O tempo para que as alterações de DNS sejam visíveis para toda a internet é de até 24 horas, segundo o próprio registro.br**

**As alterações feitas no branch gh-pages do GitHub podem demorar até 10 minutos para que tenham efeito, segundo o próprio GitHub.**


## Atenção ##
Acesse a [página de ajuda do GitHubPages](https://help.github.com/categories/20/articles) para mais informações sobre a criação de sites diferenciados para seu projeto, com templates, páginas de erro, redirecionamento, entre outras coisas.

