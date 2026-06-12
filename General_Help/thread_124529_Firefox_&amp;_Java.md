---
title: "Firefox &amp; Java"
date: 2006-02-01
forum: General Help
---

### Post by daditlefsen on 2006-02-01
Hi!

I need Java for my FireFox 1.5 so that I can pay my bills online:) I've seen on the page [https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") that I sould type this to get Java: 
> sudo apt-get install j2re1.4
But I get the message back that the file is not found..

---

### Post by o_fortuna on 2006-02-01
[QUOTE=daditlefsen]Hi!

I need Java for my FireFox 1.5 so that I can pay my bills online:) I've seen on the page [https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") that I sould type this to get Java: 

But I get the message back that the file is not found..[/QUOTE]
Make sure you have repositories enabled. The process of adding repositories is outlined [here.]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29")

Another great option is [Automatix.]("http://ubuntuforums.org/showthread.php?t=66563") Not only does it automatically update your repositories to commonly used ones, but it can automatically install several things -- like Java.

---

### Post by daditlefsen on 2006-02-02
Thanks a lot, Automatix fixed all my problems - besides ArmyOps. It wont lunch now.. :/ Error message:
> root@snuppa:~# armyops
Can't find file for package 'PixoDrv'

History:

Exiting due to error


I have tryed to uninstall it and istall it again but that didn't help mutch.. Anyone?

---

### Post by arnieboy on 2006-02-02
[QUOTE=daditlefsen]Thanks a lot, Automatix fixed all my problems - besides ArmyOps. It wont lunch now.. :/ Error message:


I have tryed to uninstall it and istall it again but that didn't help mutch.. Anyone?[/QUOTE]
u mean u tried to uninstall and reinistall automatix? or armyops?
try reinstalling armyops. 
automatix did not touch armyops but probably some library that armyops accesses got updated.

---

### Post by daditlefsen on 2006-02-02
Ive tryed to press the uninstall-file in the armyops-folder - and unistalled it. Then i installed it again (armyops250-linux.run) and now it wont work.

---

### Post by arnieboy on 2006-02-02
[QUOTE=daditlefsen]Ive tryed to press the uninstall-file in the armyops-folder - and unistalled it. Then i installed it again (armyops250-linux.run) and now it wont work.[/QUOTE]
"wont work" does not tell me much. what is the error message that u are getting?

---

### Post by daditlefsen on 2006-02-02
All of the installation goes great. And when the installation is done i open Terminal and type

root@snuppa:~# armyops

Then the spashscreen for armyops comes up, but nothing more. Then Terminal says to me:
> 
Can't find file for package 'PixoDrv'

History:

Exiting due to error

That is all i have to go on..

---

### Post by arnieboy on 2006-02-02
[QUOTE=daditlefsen]All of the installation goes great. And when the installation is done i open Terminal and type

root@snuppa:~# armyops

Then the spashscreen for armyops comes up, but nothing more. Then Terminal says to me:


That is all i have to go on..[/QUOTE]
OK I dont play armyops but I researched for u a bit and found that its an OpenGL related problem.
your armyops configuration folder is in:
$HOME/.armyops250
if u are playing version 2.50 of the game.
u can doing the following from terminal:
```
rm -rf ~/.armyops250
```
and try running the game again.
please remember that the folder will be something else like **~/.armyops251** for example if u are playing a different version of the game (like 2.51)

---

### Post by daditlefsen on 2006-02-06
Thanks, it worked:)

---

