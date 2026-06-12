---
title: "Just installed 10.10"
date: 2010-10-10
forum: General Help
---

### Post by jhanus10 on 2010-10-10
Ok well i am rather disappointed as to who did the testing on the final release.
 
Fresh install Ubuntu 10.10 reboot to Desktop went to check for updates there were 2 updates clicked install then poped up the password box typed in password and nothing happens just goes back to showing the window System Policy prevents installation..... Cancel button or Authenticate button and does nothing clicked the Authenticate button a few times nothing.
 
Dont you think this is something that might need to work so we can install updates or software?
 
Rebooted again tried installing additional drivers i get exactly the same thing as trying to update.
 
Am i missing something here?
 
Also i thought they were adding some sort of wireless driver too to the installtion but thats not seeming to work either.
 
If i am missing something on the Authenticate cool but i do know what im doing during this part its not rocket science so it should work type password then software installs.

---

### Post by jhanus10 on 2010-10-10
Heck i cant even click cancel but yet all the menus are working its not a system hang i can start and close apps

---

### Post by jhanus10 on 2010-10-10
ok closing the authenticate window using the X button then it shows Sorry, the Jockey backend crashed. Please file bug at:.............. Trying to restart backend

---

### Post by sendblink23 on 2010-10-10
Try burning again your 10.10 iso(or re-download it again - make sure when burning the ISO to use the lowest burning speed to insure a perfect burn) & install it again fresh... probably something went odd while installing on your computer

---

### Post by jhanus10 on 2010-10-10
now just tried to update again it shows the 2 updates got the same problem again where using authenticate password used X to quit then it went to installing the updates too weird!

---

### Post by DougieFresh4U on 2010-10-10
try to update through the terminal:
**Applications>Accessories>Terminal**

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by primevci on 2010-10-10
dont feel bad i cant even get a boot to install 10.10.. stuck here at 10.04 did 2 downloads 4 diffrent burns all i get is a error after splash screen...

---

### Post by jcolyn on 2010-10-10
> **primevci said:**
> dont feel bad i cant even get a boot to install 10.10.. stuck here at 10.04 did 2 downloads 4 diffrent burns all i get is a error after splash screen...


I always wipe the entire drive after backing up files to an external drive/CD/etc then start the install to a unpartitioned drive..

---

### Post by primevci on 2010-10-10
i cant even get the disk to boot to try it out has some problems mounting the file system something or another... kinda lame i was excited about this release i would wipe it but cannot get to the install.. my 10.04 boot disk boots fine

---

### Post by jcolyn on 2010-10-10
> **primevci said:**
> i cant even get the disk to boot to try it out has some problems mounting the file system something or another... kinda lame i was excited about this release i would wipe it but cannot get to the install.. my 10.04 boot disk boots fine

Have you tried burning another disk at a slower speed such as 6x??

---

### Post by jhanus10 on 2010-10-10
> **jhanus10 said:**
> now just tried to update again it shows the 2 updates got the same problem again where using authenticate password used X to quit then it went to installing the updates too weird!
 
 
Well after this incident when i closed out the auth window using the X button it successfully installed the 2 updates. Next thing i done now is installed wine 1.2 using the software manager and it went all ok so maybe the 2 updates fixd itself sofar so good.

---

### Post by sendblink23 on 2010-10-10
> **jhanus10 said:**
> Well after this incident when i closed out the auth window using the X button it successfully installed the 2 updates. Next thing i done now is installed wine 1.2 using the software manager and it went all ok so maybe the 2 updates fixd itself sofar so good.

Please uninstall that Wine version, its pretty old..

use this through TERMINAL:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.3

```
*answer yes to everything

Now you will have Wine 1.3.4

---

### Post by slooksterpsv on 2010-10-10
It wasn't the perfect 10 today like I thought it was going to be. I burned the image today and it takes forever to load into Ubuntu installer, but I was going to make a USB version of it, but that didn't go through because unetbootin wouldn't work under Kubuntu 10.10 (upgraded from 10.04) - so I've had a mess of things to configure and get working. All in all, if it crashes again tomorrow I'm heading back to Lucid.

So yeah, the slower burn, instead of wasting cds/dvds try a USB key and unetbootin.

---

### Post by primevci on 2010-10-12
> **jcolyn said:**
> Have you tried burning another disk at a slower speed such as 6x??

did it at 16x and it worked perfect thanks 16x was the lowest i could go

---

