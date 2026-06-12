---
title: "Turbo Prolog"
date: 2010-12-27
forum: General Help
---

### Post by Moawih on 2010-12-27
[[/QUOTE]**hi everyone I want to install turbo prolog complier in ubuntu 10.10 anyone have any idea?**

---

### Post by Moawih on 2010-12-27
**hi everyone I want to install turbo prolog complier in ubuntu 10.10 anyone have any idea?**

---

### Post by kaisfelfoul on 2011-02-19
** TURBO PROLOG sous UBUNTU 10.10 **

   
  Turbo Prolog est un système assez vieux Prolog qui ne fonctionne que  sous MS-DOS. Cela implique des limitations de mémoire graves. En outre,  il utilise un dialecte spécial Prolog avec des variables typées et  d'autres restrictions qui ne sont pas conformes à la norme Edinborough.  Toutefois, il est très rapide, et contient un débogueur visuelle  commode. Une fois, j'ai appris Prolog en observant ce débogueur ...

[CENTER][[IMG]http://3.bp.blogspot.com/-KMRbkrHho_c/TWBd76jTZvI/AAAAAAAAAAw/iju7sQcJTvQ/s400/prolog.png[/IMG]]("http://3.bp.blogspot.com/-KMRbkrHho_c/TWBd76jTZvI/AAAAAAAAAAw/iju7sQcJTvQ/s1600/prolog.png")[/CENTER]
[LEFT]  
Maintenant, comment installer?  Vous avez juste besoin de deux choses :



[LIST]
[*]DosBOx
[*]Turbo PROLOG  setup
[/LIST]
Pour l'installation de Dosbox, rendez-vous à votre terminal et exécutez cette ligne 

                           sudo apt-get install dosbox 

ou à partir de la Logithèque UBUNTU 


[CENTER][[IMG]http://3.bp.blogspot.com/-oG67LJAsQAM/TWBgGNd3RKI/AAAAAAAAAA0/6oVu4tpfbFQ/s640/Logith%25C3%25A8que+Ubuntu_002.png[/IMG]]("http://3.bp.blogspot.com/-oG67LJAsQAM/TWBgGNd3RKI/AAAAAAAAAA0/6oVu4tpfbFQ/s1600/Logith%25C3%25A8que+Ubuntu_002.png")[/CENTER]


  

Pour l'installation de la configuration Turbo PROLOG  setup, utilisez ce lien 

[TURBO PROLOG 2.0]("https://docs.google.com/uc?id=0BzLJKMA8XWObMTA5NzEzNmUtYzE5Zi00MTE4LWEzMjgtMTBjN2I0NjljYWJl&export=download&authkey=CJCJwIEI&hl=fr") 

[
Le paquet unrar n'est pas open source, mais devrait être capable d'ouvrir n'importe quel fichiers RAR vous pouvez trouver.

exécuter la commande suivante dans votre terminal:  sudo apt-get install unrar 
]


Maintenant, décompressez l'archive et le mettre dans votre 

DOSSIER PERSONNEL.
[CENTER][[IMG]http://3.bp.blogspot.com/-Ff4pPDj574A/TWBnbXkxsLI/AAAAAAAAABA/ciLHHbfHN4o/s400/Espace+de+travail+1_004.png[/IMG]]("http://3.bp.blogspot.com/-Ff4pPDj574A/TWBnbXkxsLI/AAAAAAAAABA/ciLHHbfHN4o/s1600/Espace+de+travail+1_004.png")[/CENTER]


[LIST]
[*]maintenant renommer "prolog".
[/LIST]


[CENTER][[IMG]http://3.bp.blogspot.com/-iQL7Sd8BnDE/TWBmjXHU_lI/AAAAAAAAAA8/qa5GeKNKLy8/s400/kaisfelfoul_001.png[/IMG]]("http://3.bp.blogspot.com/-iQL7Sd8BnDE/TWBmjXHU_lI/AAAAAAAAAA8/qa5GeKNKLy8/s1600/kaisfelfoul_001.png")[/CENTER]

il est possible que notre PROLOG.EXE demande plus de permission 


[LIST]
[*]pour  eviter le prb de 'PROLOG.EXE' ouvrer le terminal et ecrire
[/LIST]

cd ~/prolog
chmod +x PROLOG.EXE 
  

ohhhh ne réflaichit pas à cette commmande  : ./PROLOG.EXE  car la résultat est 
"err:dosmem:grin:OSMEM_MapDosLayout Need full access to the first megabyte for DOS mode"


Maintenant, ouvrez le dosbox en allant à la [COLOR=#555555][FONT=inherit]application-->games-->dosbox   [/FONT][/COLOR]
[CENTER][[IMG]http://4.bp.blogspot.com/-oD_kDWYzbgQ/TWBpLKk0_8I/AAAAAAAAABE/GtEf9b6XRfI/s320/Menu_005.png[/IMG]]("http://4.bp.blogspot.com/-oD_kDWYzbgQ/TWBpLKk0_8I/AAAAAAAAABE/GtEf9b6XRfI/s1600/Menu_005.png")[/CENTER]

 OU Ouvrez votre terminal et  écrire  : dosbox
et voici  

[CENTER][[IMG]http://1.bp.blogspot.com/-93VjQj9-HpE/TWBpXTda98I/AAAAAAAAABI/xOyKBO2ieAs/s400/DOSBox+0.74%252C+Cpu+speed%253A+++++3000+cycles%252C+Frameskip++0%252C+Program%253A+++DOSBOX_007.png[/IMG]]("http://1.bp.blogspot.com/-93VjQj9-HpE/TWBpXTda98I/AAAAAAAAABI/xOyKBO2ieAs/s1600/DOSBox+0.74%252C+Cpu+speed%253A+++++3000+cycles%252C+Frameskip++0%252C+Program%253A+++DOSBOX_007.png")[/CENTER]

 il reste un probléme  : "Dosbox" est en mode qwerty !!! c'est simple ecriver :


keyb fr
 
**TURBO PROLOG** 
mount c ~
c:
cd prolog
PROLOG.EXE


**mais à chaque fois nous allons faire tous ça pour l'exécution ?  **

**non **

fermer Dosbox et l'ouvrir de nouveau 

**Créer le fichier de configuration**
 Entrez la commande suivante:       config -writeconf prolog.conf
[CENTER][[IMG]http://2.bp.blogspot.com/-_vuJ0IBherI/TWB-Iv7IbrI/AAAAAAAAABo/Z8ppUPv3h3w/s400/ff.png[/IMG]]("http://2.bp.blogspot.com/-_vuJ0IBherI/TWB-Iv7IbrI/AAAAAAAAABo/Z8ppUPv3h3w/s1600/ff.png")[/CENTER]


fermer Dosbox maintenant  


ouvrir le fichier prolog.conf  qui  va se trouvé dans le  DOSSIER PERSONNEL
Allez à la fin du fichier, tout particulièrement la section [autoexec]  dans laquelle nous allons ajouter quelques lignes

 [autoexec]
# Lines in this section will be run at startup.
mount c ~
c:
keyb fr
cd prolog
PROLOG.EXE
# You can put your MOUNT lines here.

//supprimer se qui se trouve après cette ligne

enregister le fichier et fermer

nous allons créé un nouveau  lanceur pour notre TURBO PROLOG.

1- clique gauche en haut sur le tableau de bord "ajouter au tableau de bord" 

[CENTER][URL="http://1.bp.blogspot.com/-UsnA-3Xwyyw/TWB2xznOVoI/AAAAAAAAABM/JrM-aOHJpU8/s1600/Espace+de+travail+1_005.png"]
[/URL][/CENTER]

 2- "lanceur d'application personnaliser"


[CENTER][URL="http://3.bp.blogspot.com/-PPIQ4Yrs_9k/TWB22nM7pTI/AAAAAAAAABQ/AZwCHBP67g8/s1600/Espace+de+travail+1_007.png"]
[/URL][/CENTER]
 3- 
[CENTER][URL="http://4.bp.blogspot.com/-jJycC-nbURQ/TWB26hlvtpI/AAAAAAAAABU/VPzOOQJCigc/s1600/Espace+de+travail+1_009.png"]
[/URL][/CENTER]
4-  dans la case de commande :       dosbox -conf "prolog.conf"[/LEFT]

[CENTER]

[URL="http://1.bp.blogspot.com/-GFM_iqrQzvo/TWB5NhxZo7I/AAAAAAAAABc/-80st_H2HHk/s1600/prolog1.gif"]
[/URL][/CENTER]

 

"ALT + ENTRER"  fait le passage en mode plein écran et inversement 

et c'est tous
[CENTER][URL="http://4.bp.blogspot.com/-z47wMCgsfr4/TWB844iCoGI/AAAAAAAAABk/G_hWi51ffOA/s1600/S%25C3%25A9lection_013.png"]
[/URL][/CENTER]

---

