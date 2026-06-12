---
title: "How to install Java"
date: 2009-07-18
forum: General Help
---

### Post by xchr1s on 2009-07-18
i have a ubuntu boot USB. i want to play runescape on it. runescape requires java. how do i get it?

---

### Post by xchr1s on 2009-07-18
forgot to say in the post that i dont want to have to install ubuntu

---

### Post by doas777 on 2009-07-18
to install java, open a terminal and paste in:
```
sudo apt-get install sun-java6-jre
```

I'm not sure you will be able to play a game without a vidcard driver (which would require a reboot, hence won't work with live cd). I've never tried runescape, so no idea what sys specs it would require, but seems like an unreasonable expectation.

good luck, hope it works out for you.

---

### Post by j7%&lt;RmUg on 2009-07-18
I play runescape on 9.04 with the above package installed and it works fine, however like doas777 im not sure runescape will like running on a boot cd. Give it a go and let us know what happens.

---

### Post by _khAttAm_ on 2009-07-18
Just launch System > Admin> synaptic and then search for sun-java6-jre and install it. Hope that does it.

---

### Post by vinutux on 2009-07-18
yeh...it is better to install ubuntu instead of trying it in livecd

---

### Post by mike555 on 2009-07-18
You might like to try a live DVD made for gaming ..     [http://www.tuxmachines.org/node/6136](http://www.tuxmachines.org/node/6136)

---

### Post by The Cog on 2009-07-18
You might need to install sun-java6-plugin as well as sun-java6-jre.

My son plays runescape quite a lot on Ubuntu (installed, not from a live CD) so I confirm that it works. Except that it crashes if you try to switch to full-screen mode.

---

### Post by xchr1s on 2009-07-18
still looking for answers for livecd

---

### Post by xchr1s on 2009-07-19
still looking for answers

---

### Post by Arup on 2009-07-19
You can't install Java or anything in Live CD, reason being it doesn't write to HDD, in that case, install Ubuntu via WUBI or dual partition.

---

### Post by linux_tech on 2009-07-19
You could make a livecd/dvd  backup of your system using a program such as remastersys

---

### Post by vinutux on 2009-07-19
as i know....live cd is run on your ram as temp harddisk....so live cd is mostly used for recovering, installing, testing system capablities.....live cd is not a platform for installing programs and run games on the top of it...if you did it you need to install that programs each live session.

you need to install ubuntu to harddisk from live cd for playing that game....

---

### Post by 3rdalbum on 2009-07-19
> **Arup said:**
> You can't install Java or anything in Live CD, reason being it doesn't write to HDD,

You can install Java on the live CD, but it will install only into RAM. You'd need to activate all repositories, update the package list, and install Java every time you boot up.

The main problem is graphics card drivers - Runescape requires accelerated 3D from the looks of it. If you've got Intel graphics, you'll be okay as the default Intel driver will give you 3D acceleration out-of-the-box. If you have a graphics card or graphics chipset from almost any other vendor, it will not be able to work from the live CD.

I'd still recommend installing Ubuntu, even if just onto a flash drive.

---

### Post by The Cog on 2009-07-19
> **xchr1s said:**
> still looking for answers

What's wrong with the answers you have already been given? Have you tried them?

---

### Post by xchr1s on 2009-07-19
i want to know about the boot usb i dont care about doing it from the live cd!!!!!!!!!!

---

### Post by The Cog on 2009-07-19
The answers apply to both CD and USB boot. 
> sudo apt-get install sun-java6-jre sun-java6-plugin
and unless you have set up the USB stick for persistent filesystem changes you will have to do it every time you boot.

---

### Post by doas777 on 2009-07-20
I'm sorry, what you want is most likely not possible. if you can't install drivers, you are sunk. perhaps installing to a thumbdrive might work, but seriously, this is an unreasonable request.

---

### Post by xchr1s on 2009-07-22
do does sudo apt-get install sun-java6-jre sun-java6-plugin work on boot usb?

---

### Post by michy99 on 2009-07-22
Is your USB a persistent install that can save changes? If not, look at this to see how to make one:

[http://webupd8.blogspot.com/2009/07/how-to-install-and-run-ubuntu-904.html](http://webupd8.blogspot.com/2009/07/how-to-install-and-run-ubuntu-904.html)

Whether this will work for your purposes or not, I really don't know.

---

