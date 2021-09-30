# A01 - Introducció a git

## Índex: Elements bàsics

- Introducció
- Orígens de git
- Conceptes importants de git
- Instal·lació i configuració bàsica
- Ignorant fitxers: .gitignore
- Creació del primer repositori

## Introducció

### Com compartim el codi?

Un **equip** de desenvolupadors pot estar format per un enginyer que dissenya el programa, diversos programadors que programen el codi, un testejador que fa les proves d'integració i de qualitat, entre d'altres.

Els membres d'un equip de desenvolupament necessiten **compartir** el codi i altres fitxers. Com ho fan?

- Amb fitxers adjunts al correu... NO!!
- Amb un disc al núvol tipus Google Drive o Dropbox... NO!!
- etc ... NO!!

- **Usen GIT** !!

> **GIT és un _Sistema de Control de Versions_ (VCS o _Version Control System_) que permet compartir fitxers entre tots els membres d'un equip, controlant i gestionant les diferents versions que es van generant amb el pas del temps.**

Què fa git per vosaltres?

- Controla les versions dels fitxers i controla el codi font
- Fa un seguiment de tots els canvis enviats al _codebase_
- Reverteix els canvis
- Crea branques noves sense afectar les branques amb versions estables
- Indica quan hi ha conflictes de fusió de versions

Per què git?

- Perquè "tothom" l'utilitza
- És probable que l’utilitzeu quan obtingueu una feina
- És gratuït
- És de codi lliure

## Orígens de git

> Git va ser creat l'any 2005 per Linus Torvalds, el creador de Linux. És un projecte de codi obert i lliure.

## Conceptes importants de git

Git permet que un servidor remot allotgi el vostre repositori (repo).

Tots els usuaris mantenen una còpia local de tots els seus repos.

Cal instal·lar git, tot i que les distribucions de linux ja el solen tenir instal·lat per defecte.

<img src="./images/git01.png" alt="git" width="600"/>

* Git és una col·lecció de moltes eines
* Ha evolucionat a partir de llenguatges de guions (_scripts_)
* És adequat a la mentalitat d’un programador de C
* Tot està exposat i és accessible
* És molt flexible
* **Cal entendre el model subjacent**

> Git té **moltes** comandes

Aprèn inicialment només les més importants.

Aprèn la resta de comandes a mesura que les vagis necessitant.

### Grups de comandes git

- De creació i gestió de branques:
    * init, checkout, branch
- De modificació:
    * add, delete, rename, commit
- D'obtenció d'informació:
    * status, diff, log
- Per a la creació de punts de referència:
    * tag, branch

### El codi font

El codi font (o _source code_) és l'element principal d'un desenvolupament de programari. Està format per fitxers i carpetes, i es gestiona amb git.

> La carpeta mare on s'ubica el codi font d'un programa s'anomena ```src``` i conté els fitxers i carpetes de tot el projecte de desenvolupament d'una aplicació. La gran majoria de fitxers contindran codi en un llenguatge de programació d'alt nivell, com ara java.

### Repositori git

Una carpeta o directori pot contenir altres directoris i fitxers.

> Un repositori és un directori que conté fitxers (inclosos altres directoris) i també conté _commits_.

La gestió dels _commits_ es fa amb git i git guarda tota la informació que necessita (per a gestionar el repositori) en un subdirectori ocult anomenat ```.git```. Diem que aquest subdirectori ```.git``` conté les metadades del repositori.

<img src="./images/git02.png" alt="git" width="300"/>

> Un directori es pot transformar en un repositori git inicialitzant-lo amb la comanda ```git init```.

Un repositori git també guarda **totes les relacions entre les diferents versions dels fitxers al llarg del temps**:

<img src="./images/git03.png" alt="git" width="300"/>

## Instal·lació i configuració bàsica

Git ja ve instal·lat per defecte en la gran majoria de distribucions linux.

En un debian, per exemple, es pot instal·lar així:

```bash
$ sudo apt install git
```

Abans de començar a treballar amb git, n'hem de fer una configuració mínima:

- Configuració global: serveix per a tots els repositoris que creem.
- Configuració pròpia per a cada repositori.

Usarem una configuració global, que serà la que tindrem per defecte i que s'aplicarà a tots els repositoris que creem. Això no impedeix crear una configuració específica per a un repositori en particular si així ho necessitem.

Cal configurar com a mínim els següents dos paràmetres: el nom, i l'adreça de correu electrònic. Les següents comandes es poden executar des de qualsevol ubicació dins del sistema:

```bash
$ git config --global user.name "Jordi Casamitjana Querol"
$ git config --global user.email "jcasamq@domini.cat"
```

Les comandes per a fer una configuració específica per a un repositori en concret són les mateixes, però sense l'opció ```--global```. En aquest cas, serà necessari executar-les dins del repositori.

Si ja tenim un compte a github o gitlab, és recomanable també configurar el nom d'usuari del nostre compte de github o gitlab:

```bash
$ git config --global user.username "jcasamq"
```

En aquest darrer cas (si tenim un compte de github o gitlab) també configurarem l'adreça de correu i el nom perquè coincideixi amb els del nostre compte.

## Ignorant fitxers: .gitignore

Dins d'un repositori git, tots els fitxers estan sotmesos a git. Però si ens interessa que algun fitxer o directori no ho estigui, el podem incloure en un fitxer especial, anomenat ```.gitignore``` que serveix precisament per a això: **tot fitxer o directori inclòs a .gitignore no serà tingut en compte per git**.

> És convenient no incloure el mateix fitxer .gitignore dins de .gitignore, ja que convé que git no ignori el fitxer ```.gitignore```.

Podeu trobar informació sobre com es configura el fitxer .gitignore en el següent enllaç:

<a href="https://www.tremplin-numerique.org/ca/quest-ce-quun-fichier-gitignore-et-comment-le-configurer" target="_blank">Què és un fitxer .gitignore i com el puc configurar?</a>

## Exercici: Creació del primer repositori

Suposem que ja tenim git instal·lat. En cas contrari, l'instal·leu segons quin sigui el vostre sistema operatiu. Anteriorment hem vist un exemple de com instal·lar-lo en una distro Debian:

```bash
$ sudo apt install git
```

**Obriu un terminal en el vostre entorn de treball.**

- Primer pas: establir la configuració global

Si ja teniu un compte a Github o Gitlab, heu de fer servir les mateixes dades que hi teniu per fer la configuració local:

```bash
$ git config --global user.name "Jordi Casamitjana Querol"
$ git config --global user.email "jcasamq@domini.cat"
$ git config --global user.username "jcasamq"
```

Per a comprovar la configuració que tenim, podem executar:

```bash
$ git config -l
user.name=Jordi Casamitjana Querol
user.email=jcasamq@domini.cat
user.username=jcasamq
```

Els valors de configuració que no hem establert nosaltres, tenen uns valors per defecte, que no caldrà canviar.


- Segon pas: establir el directori de treball

Per fer totes les proves i exercicis d'aquest curs de git, crearem un directori anomenat git en el vostre ```$HOME```. Aquest directori serà el nostre directori de treball:

```bash
$ mkdir ~/git
$ cd ~/git
```

- Tercer pas: establir el directori matriu del repositori

En el nostre directori de treball, crearem un subdirectori anomenat ```exemple1_git```:

```bash
~/git$ mkdir exemple1_git
~/git$ cd exemple1_git
```

Aquest nou directori està buit, doncs l'acabem de crear. Això ho podem comprovar amb la comanda ```ls -a```:

```bash
~/git/exemple1_git$ ls -a
.  ..
~/git/exemple1_git$
```

- Quart pas: inicialitzem el repositori git

Inicialitzem aquest directori com a repositori git. Des de dins del mateix directori, hi executem ```git init```. Un cop completada la comanda, si llistem el contingut del directori, ara ja hi veurem el subdirectori ```.git``` (que conté les metadades de git):

```bash
~/git/exemple1_git$ git init
Initialized empty Git repository in /home/jcasamq/git/exemple1_git/.git/
~/git/exemple1_git$ ls -a
.  ..  .git
~/git/exemple1_git$
```

- Cinquè pas: creem el fitxer ```.gitignore```

A continuació hi crearem el fitxer ```.gitignore```, encara que de moment no el farem servir, convé tenir-lo present des de bon inici:

```bash
~/git/exemple1_git$ touch .gitignore
~/git/exemple1_git$ ls -a
.  ..  .git  .gitignore
~/git/exemple1_git$
```

- Sisè pas: creem el fitxer README.md

Tot repositori git convé que tingui un fitxer anomenat ```README.md```. Aquest és un fitxer _markdown_ que té per finalitat donar informació bàsica sobre els continguts del repositori.

Un fitxer _markdown_ es pot crear i editar des del terminal de linux, usant els editors ```vi``` o ```nano``` (entre d'altres) o bé es pot crear i editar usant l'entorn _Jupyter Lab_:

```bash
~/git/exemple1_git$ vi README.md

# El meu primer exemple de repositori git

~/git/exemple1_git$ ls -a
.  ..  .git  .gitignore  README.md
~/git/exemple1_git$
```

Si feu servir l'entorn _Jupyter Lab_ abans de crear el fitxer README.md, us heu d'ibicar en el directori on el voleu crear (a ```~/git/exemple1_git``` en aquest cas). Hi escriviu el següent contingut i guardeu els canvis (ctrl+s):

```
# El meu primer exemple de repositori git
```

- Setè pas: comprovem l'estat del nostre repositori

Amb la comanda ```git status``` obtenim informació sobre en quin estat es troba el nostre repositori:

```bash
~/git/exemple1_git$ git status

On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        README.md

nothing added to commit but untracked files present (use "git add" to track)

~/git/exemple1_git$ 
```

En properes activitats aprendrem a entendre el significat d'aquest missatge.

