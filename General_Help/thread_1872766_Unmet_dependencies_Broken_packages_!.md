---
title: "Unmet dependencies Broken packages !"
date: 2011-10-31
forum: General Help
---

### Post by shaon3343 on 2011-10-31
[SIZE=2][B]Hello there,I'm Using ubuntu 10.10 , I installed [Kile]("http://kile.sourceforge.net/") by creating my own local repository today . after that installation I re-enabled those ubuntu package-repositories and ran a sudo apt-get update . I was intended to install [Calibre]("http://packages.ubuntu.com/maverick/calibre") but its showing me an unmet dependencies error with Broken package !
> munna@munna-Inspiron-1545:~$ sudo apt-get install calibre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:[/B][B]
 calibre : Depends: python-qt4 but it is not going to be installed
E: Broken packages
I executed sudo apt-get install -f and sudo apt-get check but it dosen't replied any clue ! 
>  munna@munna-Inspiron-1545:~$ sudo apt-get check
[sudo] password for munna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
 >  munna@munna-Inspiron-1545:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 Please tell me how can I fix it and install Calibre . Thanks in advance.[/B][/SIZE]

---

### Post by Gremlinzzz on 2011-10-31
:popcorn:
[http://www.ehow.com/how_8447960_fix-broken-packages-ubuntu.html](http://www.ehow.com/how_8447960_fix-broken-packages-ubuntu.html)

---

### Post by shaon3343 on 2011-10-31
> **Gremlinzzz said:**
> :popcorn:
[http://www.ehow.com/how_8447960_fix-broken-packages-ubuntu.html](http://www.ehow.com/how_8447960_fix-broken-packages-ubuntu.html)

[SIZE=2][B]Thanks a bunch for your help but It didn't work ! it showed the attached message ! I did try to install python-qt4 but it also showed same kind of message regarding
other dependencies! It looks like My UBUNTU is just filled with a chain of Dependency Problem ! Please Help me out of this.[/B][/SIZE] [SIZE=2]**Thanks again**[/SIZE].

---

### Post by Gremlinzzz on 2011-10-31
do you have these check in software sources?

 [http://ubuntuforums.org/attachment.php?attachmentid=205964&stc=1&d=1320072243](http://ubuntuforums.org/attachment.php?attachmentid=205964&stc=1&d=1320072243)

if not do it then sudo apt-get update

---

### Post by cavalier911 on 2011-10-31
Aptitude's resolver will propose solution's to fix the unmet dependencies.
You may need to add the repository with the package version required to fix the issue.
```
sudo aptitude
```
The mouse opens a menu, ctrl+t closes menus.
ctrl+t toggles menu , F6/F7 toggle's window tabs, q closes out a window, ? opens Help tab.

---

### Post by shaon3343 on 2011-11-01
Thanks a lot to all of you ! Its Solved ! I just searched on the web and added all those [attached epositories]("http://ubuntuforums.org/attachment.php?attachmentid=206011&stc=1&d=1320121164") and after a sudo-apt-get update all problems are solved ! Cheers !:popcorn:  :guitar:  :guitar:

---

