# Bioinformática {#bioinf}



Nesse capítulo é apresentado como instalar programas de Bioinformática.

## Instalar ambiente estatístico R

As distribuições Ubuntu e Debian possuem o programa R pronto para ser instalado via Internet usando o gerenciador de pacotes `apt-get` (ou `aptitude`), entretanto a versão do programa R disponível é desatualizada.
Para obter a versão mais atual do programa R é preciso adicionar a fonte de pacotes do CRAN usando algum _mirror_ oficial e editar o arquivo de configuração do sistema localizado em `/etc/apt/sources.list`.
  
Adicionar a fonte de pacotes, nesse caso é utilizado o _mirror_ oficial da [FMVZ USP](http://www.vps.fmvz.usp.br/CRAN/).
A lista de mirrors oficials esta disponível [aqui](http://cran.r-project.org/mirrors.html).
O texto a segir deve ser adicionado no final do arquivo `/etc/apt/sources.list`.

    # R repositories - lasted package versions
    deb http://www.vps.fmvz.usp.br/CRAN/bin/linux/ubuntu xenial/
  
Após salvar as alterações no arquivo é necessário atualizar a lista de pacotes do gerenciador.


```bash
sudo apt-get update
```
  
Haverá um aviso sobre a identidade da nova fonte de pacotes, para resolver é necessário fazer a autenticação. Esse passo é opcional.


```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
```

Pronto. Agora instalar o programa R e suas dependências.


```bash
sudo apt-get install r-base-dev
```

É recomendado instalar os pacotes do R dentro do ambiente usando a função `install.packages` pois eles estão mais atualizados.
Fazer isso como usuário comum, assim os pacotes instalados ficam no diretório pessoal do usuário e não interfere na administração do sistema.

## Instalar RStudio Server

Passo a passo para instalação do programa estatístico _R_ e o progrma _RStudio_ versão servidor. O _RStudio Server_ é executado no sistema operacional como um serviço, sua IDE (interface de desenvolvimento integrado) é acessado a partir do navegador Web, todo o processamento é executado na maquina servidora. A autenticação da IDE é feita utilizando informações de usuários de sistema, vários usuários podem utilizar o ambiente de desenvolvimento simultaneamente.

Essa configuração é recomendada para ambientes multiusuários onde os computadores Desktop não possuem recurso computacional (processador, memória RAM e disco) suficiente para executar as análises em R. Também existe a versão Desktop do _Rstudio_, mais informações no [site oficial](http://www.rstudio.com/products/RStudio/).

O tutorial foi testado no sistema operacional _Ubuntu Server 14.04.1_ disponível para [Download](http://www.ubuntu.com/download/server).

Primeiro resolver uma dependencia do sistema.

    sudo apt-get install libapparmor1 libssl0.9.8
  
Depois baixar o arquivo `.deb` e instalar.


```bash
wget https://download2.rstudio.org/rstudio-server-1.0.136-amd64.deb
sudo dpkg -i rstudio-server-1.0.136-amd64.deb
```

É recomendado acessar o site oficial e baixar a versão mais atual do programa encontrado [aqui](http://www.rstudio.com/products/rstudio/download-server/). Para acessar a IDE pelo navegador acesse o IP da maquina, porta 8787.

## Pacotes extras (opcional)

Alguns pacotes do sistema poderão ser necessários ao trabalhar com determinados pacotes do R.


```bash
sudo apt-get install libcurl4-openssl-dev ghostscript libxml2-dev
```

Para gerar arquivos PDF de documento R Markdown e Sweave é preciso instalar o _TeX Live_ no sistema, isso exige espaço em disco considerável.


```bash
sudo apt-get install texlive texlive-latex-extra texlive-fonts-extra texinfo
```

Para concluir instalar o git.
O Rstudio tem integração com programas de versionamento de códigos.


```bash
sudo apt-get install git
```