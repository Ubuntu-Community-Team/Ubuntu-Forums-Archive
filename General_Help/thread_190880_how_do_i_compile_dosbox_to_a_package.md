---
title: "how do i compile dosbox to a package?"
date: 2006-06-06
forum: General Help
---

### Post by graigsmith on 2006-06-06
i figured out how to compile it, but how do i compile it to an easy to install and uninstall package?

---

### Post by Skye on 2006-06-06
You would use a package called "checkinstall", which instead of installing a compiled package through make install, it creates a .deb package and installs that.  First, you need to install it. Run this in a terminal: ```
sudo apt-get install checkinstall
```
After it installs, configure dosbox as you normally would using ./configure and make.  But, install of running **make install**, you would run **sudo checkinstall**.  From there on out, it's pretty much self-explainatory, but feel free to ask questions if you have any.

---

### Post by vyruss on 2006-06-06
[QUOTE=graigsmith]i figured out how to compile it, but how do i compile it to an easy to install and uninstall package?[/QUOTE]

What's wrong with the version in the repositories?

---

### Post by graigsmith on 2006-06-06
the version in the repositories, is old.

---

### Post by graigsmith on 2006-06-06
checkinstall worked great :)

---

### Post by Skye on 2006-06-06
Glad to hear it. :D

---

### Post by graigsmith on 2006-06-15
Checkinstall KILLED my computer. lol.

thankfully my home partition did not get messed up. 

im not sure what i did to mess up my system.  first of all my system partition was using ext2.  mabey that's why it got corrupted.  Though im not totally sure it was corrupted, but it wouldn't let me log in.  but anyways what i did to crash my system was this. 

i downloaded amule sources, and ran ./configure on them.  then i forgot to run make, and ran checkinstall instead.  started getting errors, and stuff, and figured i ought to run make first.  so i hit ctrl-c to cancel.  it cancelled. and stuff started crashing immediately.  gnome panel died, along with various other things. decided to kill x, to see if that would fix it.  

x failed to start,  tried to log into the text command.  it said.  login failed. /home/graig not found.  so i rebooted.  still no x, still no login.  I thought my home partition was gone. :shock:

so i had to format my system partition.  this time i went with ext3 on my main system partition. and im not going to mess with compiling amule ever again. [-(   it took about a minute to boot up to the new ubuntu install cd.  once i was on the desktop.  and after i went through the install config to select the partitions not to delete.  had it use my existing home folder. had it format my system partition.   But the *Amazing* thing is that when i hit go to start installing it, it took **7!!! minutes!!!** i was shocked..  never since beos have i seen an os install so fast.  after that, it took about 10 minutes to install about 30 or so programs that i used.  

if this was a windows crash, i would still be fixing stuff.  I love ubuntu.  :-P

so, the moral is, be careful when using checkinstall, or when using sudo.  and also, always put your home folder on a seperate partition, it will save you.

---

### Post by Bokonon on 2006-06-16
I guess the moral of the story is that it works great if you follow the directions, but if not....BOOM!!  :-({|=

---

### Post by mlind on 2006-06-16
fakeroot is amazing program to prevent mocups like these :mrgreen:

---

