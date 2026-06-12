---
title: "ubuntu-tweak"
date: 2010-07-02
forum: General Help
---

### Post by Veector on 2010-07-02
After i tried to install the ubuntu tweak .deb on ubuntu 64 bit, I get this error when ever i try to sudo apt-get upgrade or sudo apt-get install something.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-tweak (0.5.4.1-1~lucid1) ...
Warning: /usr/share/gconf/schemas/uturl.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing ubuntu-tweak (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)

I really need help, what can i do to fix this?

---

### Post by Veector on 2010-07-02
right now i can't install software at all

---

### Post by dino99 on 2010-07-02
goto system admin synaptic to install what you need

---

### Post by Veector on 2010-07-02
I cant install or update my system because when ever i try to do so i get the error that i posted above

---

### Post by philinux on 2010-07-02
> **Veector said:**
> I cant install or update my system because when ever i try to do so i get the error that i posted above

Try this 

```
sud dpkg --configure -a
```

Post back all errors.

---

### Post by Veector on 2010-07-02
when i enter that nothing happens

---

### Post by Rubi1200 on 2010-07-02
> **Veector said:**
> when i enter that nothing happens

Hi, no disrespect intended to philinux, but there is a typo:

The command you need to enter in the terminal is:

```
sudo dpkg --configure -a
```

Try this and post back any errors you get.

---

### Post by Veector on 2010-07-02
I did notice that sudo was miss spelled but it still gives back no errors.

---

### Post by Veector on 2010-07-03
When I run this code nothing happens, I am not able to install or update my system, because i get this message 
> victor@victor-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-tweak (0.5.4.1-1~lucid1) ...
Warning: /usr/share/gconf/schemas/uturl.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing ubuntu-tweak (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
Just because i tried to install ubuntu-tweak

---

### Post by Darkness Des on 2010-07-03
Try
```

sudo apt-get install -f

```
That fixes broken packages. It SHOULD work.

---

### Post by Veector on 2010-07-03
When i input that command this is what i get back 

> victor@victor-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ubuntu-tweak (0.5.4.1-1~lucid1) ...
Warning: /usr/share/gconf/schemas/uturl.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing ubuntu-tweak (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mjneil.81 on 2010-07-03
did you use 
> sudo add-apt-repository ppa:tualatrix/ppa
as the repo

---

### Post by philinux on 2010-07-03
> **Rubi1200 said:**
> Hi, no disrespect intended to philinux, but there is a typo:

The command you need to enter in the terminal is:

```
sudo dpkg --configure -a
```

Try this and post back any errors you get.

At least with sud it might have cleaned things up. :mrgreen:

---

### Post by warfacegod on 2010-07-03
This is unlikely to work but it's worth a shot:

```
sudo apt-get purge ubuntu-tweak
```

```
sudo apt-get autoremove
```

You may also want to clear your cache.

I ran into this once before and it was my own fault not Ubuntu Tweak's. I accidentally tried to install the Intel version into an AMD machine. I'm pretty sure I just ended up reinstalling Ubuntu. It was getting to be time and that's what I wanted Ubuntu Tweak for, to help get cleaned up, so I didn't have to reinstall just yet.

---

### Post by Detonate on 2010-07-03
Instead of installing ubuntu-tweak, you may want to try a program named ailurus. See this:
[http://www.ubuntugeek.com/how-to-install-ailurus-10-01-in-ubuntu-kubuntu-xubuntu.html](http://www.ubuntugeek.com/how-to-install-ailurus-10-01-in-ubuntu-kubuntu-xubuntu.html)
I find it does everything ubuntu-tweak does, and more.  It's a great utility.

---

### Post by philinux on 2010-07-03
If warfacegod solution not fixing it then try this.

Similar, so substitute your package. See post 18 and 19.
[http://ubuntuforums.org/showthread.php?p=9517069#post9517069](http://ubuntuforums.org/showthread.php?p=9517069#post9517069)

---

### Post by Veector on 2010-07-03
Post number 19 did it for me, thanks for all of your help guys

---

