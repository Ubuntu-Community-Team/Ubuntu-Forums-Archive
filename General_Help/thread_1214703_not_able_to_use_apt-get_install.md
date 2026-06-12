---
title: "not able to use apt-get install"
date: 2009-07-16
forum: General Help
---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
having attempted to get dvd playback on the computer,I followed the guide in the multimedia forum, only to get terminal stuck on the configure package screen (blue screen with Sun EULA on it, with OK at the bottom, but nothing happens when you try enter, or any similar comands)

having restarted the computer,  attempted to install Wine. and get this message

> ben@ben-desktop1:~$ sudo apt-get install wine
[sudo] password for ben: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
ben@ben-desktop1:~$ 
ben@ben-desktop1:~$ 
ben@ben-desktop1:~$ sudo dpkg --configure -a
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
ben@ben-desktop1:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  ia32-sun-java6-bin: Depends: sun-java6-jre (= 6-14-0ubuntu1.9.04) but it is not going to be installed
                      Recommends: lib32nss-mdns but it is not going to be installed
  wine: Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
        Recommends: ttf-liberation but it is not going to be installed
        Recommends: winbind but it is not going to be installed
        Recommends: wine-gecko but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ben@ben-desktop1:~$ sudo apt-get -f install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  ia32-sun-java6-bin: Depends: sun-java6-jre (= 6-14-0ubuntu1.9.04) but it is not going to be installed
                      Recommends: lib32nss-mdns but it is not going to be installed
  wine: Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
        Recommends: ttf-liberation but it is not going to be installed
        Recommends: winbind but it is not going to be installed
        Recommends: wine-gecko but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ben@ben-desktop1:~$ 


what do I need to do.

(ubuntu 9.04 x86-64, quadcore (4*3GHz) 8GB DDR2 800, 1TB SATA2 hard disk)

---

### Post by nikhilk on 2009-07-16
Do you need java? If yes, try re-installing that or else un-install it as that seems to be causing the problem.

---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
> **nikhilk said:**
> Do you need java? If yes, try re-installing that or else un-install it as that seems to be causing the problem.

thats the file I got following the first bit of the guide here
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and I want the PC to play dvd's so assuming I need that java file to make that run

---

### Post by blazemore on 2009-07-16
Have you tried running
```
sudo apt-get -f install
```

---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
> **blazemore said:**
> Have you tried running
```
sudo apt-get -f install
```

I have. and it runs as follows

> ben@ben-desktop1:~$ sudo apt-get -f install wine
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
ia32-sun-java6-bin: Depends: sun-java6-jre (= 6-14-0ubuntu1.9.04) but it is not going to be installed
Recommends: lib32nss-mdns but it is not going to be installed
wine: Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
Recommends: ttf-liberation but it is not going to be installed
Recommends: winbind but it is not going to be installed
Recommends: wine-gecko but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ben@ben-desktop1:~$ 

---

### Post by CatKiller on 2009-07-16
> **PsYcHoTiC_MaDmAn said:**
> I have. and it runs as follows

That isn't what blazemore (and that error message, for that matter) said to run.

---

### Post by mcduck on 2009-07-16
> **PsYcHoTiC_MaDmAn said:**
> I have. and it runs as follows

use just the "sudo apt-get -f install" first to fix the situation.

And what comes to the Sun Java's EULA screen you'll have to press Tab key to select the OK-button, and then Enter.

---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
> **CatKiller said:**
> That isn't what blazemore (and that error message, for that matter) said to run.

ok, its fairly obvious what I thought he meant...

> ben@ben-desktop1:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ben@ben-desktop1:~$ 


---

### Post by carml on 2009-07-16
By the way you don't need Java to play dvd,to do so install the medibuntu package as follow```
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update 

```
and ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
These commands should be also on the link you gave on your post.

---

### Post by PsYcHoTiC_MaDmAn on 2009-07-16
> **carml said:**
> By the way you don't need Java to play dvd,to do so install the medibuntu package as follow```
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update 

```
and ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```
These commands should be also on the link you gave on your post.

well dont know whats happened, but I've got dvds playing via VLC, (from the guide) and its now installing wine via the apt-get install

---

### Post by carml on 2009-07-16
If you typed the command I gave you,you installed the missing codecs to play DVDs etc,and you ald (with the last commaand) imported the key to prove the packages came from a trusted repository. :)

---

### Post by CatKiller on 2009-07-16
> **PsYcHoTiC_MaDmAn said:**
> ok, its fairly obvious what I thought he meant...

Of course. I was just letting you know why what you'd put in hadn't done what you'd hoped. Glad you've got your package management working again now.

---

