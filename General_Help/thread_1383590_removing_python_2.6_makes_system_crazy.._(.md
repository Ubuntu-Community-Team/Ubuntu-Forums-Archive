---
title: "removing python 2.6 makes system crazy.. :("
date: 2010-01-17
forum: General Help
---

### Post by Hajex on 2010-01-17
Hi all ..
I did some stupid steps by removing python 2.6
I just try to use python 2.5 only 
after removing , all icons  disappeared and I couldn't shut down ..so I reinstalled python 2.6 again.
I try to restart system but grub menu display _debian instead of ubuntu _(how could this happened I don't use debian ) . I try to log in console but also keyboard is not working and only allow me to use numbers so I couldn't login .
I try to startup from usb but also not allow me:( 
my system is ubuntu 9.10

please help me ..
is there any way to login and repair this package ? 
if not is there any way to extract files from hard disk ???

I need this files how can I recover them ?:(

---

### Post by n0dix on 2010-01-17
You can login in Tty console??
Try:
```
sudo apt-get install ubuntu-desktop python
```

It's NOT recommended to remove python because it provides some important fetures.

---

### Post by LumbeeNDN on 2010-01-17
...I feel your pain Hajex!!!

[http://ubuntuforums.org/showthread.php?t=1383588](http://ubuntuforums.org/showthread.php?t=1383588)

...going to try ndix suggestion...

---

### Post by n0dix on 2010-01-17
See a related post: [http://ubuntuforums.org/showthread.php?t=785928&page=2]("http://ubuntuforums.org/showthread.php?t=785928&page=2")

---

### Post by gradinaruvasile on 2010-01-17
Well that was terrible idea. You should have linked python 2.5 to python instead  of 2.6...

PS. If you used NetworkManager to connect to the internet... I think that its gone too so you cant connect to the internet, only with ifconfig.

---

### Post by LumbeeNDN on 2010-01-17
...thanx for the links and info ndix...the desktop is running now...hopfully this will fix me up...

---

### Post by LumbeeNDN on 2010-01-17
> **gradinaruvasile said:**
> Well that was terrible idea. You should have linked python 2.5 to python instead  of 2.6...

...how are we supposed to know phython is this tightly wound with the system? The 2.6 version of python has some bugs when you are running code from the console, so I thought I'd just do a different install of python. I had no idea it screwed with anything but the python console. Now I know, but for folks coming from the Windows world is a little different...

---

### Post by blackened on 2010-01-17
> **LumbeeNDN said:**
> ...how are we supposed to know phython is this tightly wound with the system? The 2.6 version of python has some bugs when you are running code from the console, so I thought I'd just do a different install of python. I had no idea it screwed with anything but the python console. Now I know, but for folks coming from the Windows world is a little different...

That's the reason you have to supply a password when removing packages: the system expects you to know what you're doing.

As an analogy, this would be equivalent to haphazardly deleting entire swaths of dll files from the Windows directory and then acting incredulous when the system is fubar'd.

Ok, that's not entirely true since 8.04 didn't ship with python 2.6, so it would be more like installing a service pack and then expecting the system to be fine after deleting significant portions of said service pack.

---

### Post by LumbeeNDN on 2010-01-17
...hey ndix, that worked, I'm back up now...thanx for the good info, and not calling me an idiot...

---

### Post by n0dix on 2010-01-17
You're welcome. 

Btw don't do that again. :twisted:

Add the SOLVED tag to the tittle

---

### Post by Hajex on 2010-01-17
ok let's back ..
PROBLEM not solved yet:(
really I can't login .. keyboard does not allow me to enter any thing just numbers ..what can I do for that ??

if I use live CD .. how can I login to system from there ?? :(

---

### Post by HighCommander540 on 2010-01-17
> **Hajex said:**
> ok let's back ..
PROBLEM not solved yet:(
really I can't login .. keyboard does not allow me to enter any thing just numbers ..what can I do for that ??

if I use live CD .. how can I login to system from there ?? :(

If you have a live CD why don't you just reinstall the system?

---

### Post by Hajex on 2010-01-17
I need most of the files ..
I want to understand how can I get these files ..I just can access them but not read or copy .. is there any way to read them by last username and pw

---

### Post by n0dix on 2010-01-17
You try the Tty console login??

---

### Post by Hajex on 2010-01-17
once system boot ... it directly displays tty login but I can't login at all .. I only can use numbers keys while letters keys are not working at all

---

### Post by n0dix on 2010-01-17
Use the livecd and do a backup of your files. Then reinstall ubuntu. 

Mount your partition and do a backup:
```
$ sudo mkdir /media/ubuntu
```
Mount the volume:
```
$ sudo mount /dev/sdaX /media/ubuntu
```
Where the X is the number of you / partition. This depends on where is the info you want to backup up.

---

### Post by Hajex on 2010-01-17
Thanks n0dix and all of u guys ..
I think I will do that  but I'm still sure there is a solution with out reinstallation ..

I still want to know :
**why grab menu display debian instead of ubuntu ? is this meaning ubuntu is demaged once python is removed??

** I reinstall python 2.6  at the same time when removing .. why this step is not working?

** I can access most of files from liveCD so what is the meaning of  username and PW ?? means any one can  access my files just using liveCD ?

**Don't call any one stupid , if u have a good solution then say otherwise keep bad words in ur mouth ..

** Thanks for all but I don't believe that formatting is only solution for any problems .. thanks all of u guys..

---

### Post by Nathic on 2010-12-15
To everybody who did the same mistake as me (sudo aptitude remove python) ;D

This is how I solved the Problem

if you don't have a screen try CTRL+ALT+F3

First I tried all these commands:

> 
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove

Then I found out that I wasn't connected to a network

>  sudo dhclient

and then

> sudo aptitude install ubuntu-desktop python 


Hope that helps you

---

