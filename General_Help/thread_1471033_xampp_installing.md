---
title: "xampp installing"
date: 2010-05-03
forum: General Help
---

### Post by honnour on 2010-05-03
Hi,

I'm a new linux user. I'm trying to install xampp to my ubuntu.I've downloaded the necessery file.Then i started to follow the instructions at
[http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

but
there is line at that manuel that tells me to write
"tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt"  to terminal.When i wrote it i have the following problem;

tar: xampp-linux-1.7.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

What should i do to fix this problem? or Do you have any suggestions to install xampp to ubuntu?

Thank you very much for your helps.

---

### Post by dino99 on 2010-05-03
> **honnour said:**
> Hi,

I'm a new linux user. I'm trying to install xampp to my ubuntu.I've downloaded the necessery file.Then i started to follow the instructions at
[http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

but
there is line at that manuel that tells me to write
"tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt"  to terminal.When i wrote it i have the following problem;

tar: xampp-linux-1.7.3a.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

What should i do to fix this problem? or Do you have any suggestions to install xampp to ubuntu?

Thank you very much for your helps.

check the real file name, then untar with full path to that file (where you have downloaded it)

[http://www.linuxinet.com/free-linux-software/xampp-1-7-1-run-your-own-website-local-pack-easily-installation.html](http://www.linuxinet.com/free-linux-software/xampp-1-7-1-run-your-own-website-local-pack-easily-installation.html)
[http://www.secuobs.com/secumail/btsecumail/msg18373.shtml](http://www.secuobs.com/secumail/btsecumail/msg18373.shtml)

[http://minez-inspirate.blogspot.com/2009/05/install-xampp-17-in-ubuntu-904.html](http://minez-inspirate.blogspot.com/2009/05/install-xampp-17-in-ubuntu-904.html)

---

### Post by honnour on 2010-05-03
> **dino99 said:**
> check the real file name, then untar with full path to that file (where you have downloaded it)

[http://www.linuxinet.com/free-linux-software/xampp-1-7-1-run-your-own-website-local-pack-easily-installation.html](http://www.linuxinet.com/free-linux-software/xampp-1-7-1-run-your-own-website-local-pack-easily-installation.html)
[http://www.secuobs.com/secumail/btsecumail/msg18373.shtml](http://www.secuobs.com/secumail/btsecumail/msg18373.shtml)

[http://minez-inspirate.blogspot.com/2009/05/install-xampp-17-in-ubuntu-904.html](http://minez-inspirate.blogspot.com/2009/05/install-xampp-17-in-ubuntu-904.html)


yeah the file that i downloaded is on my desktop, not in opt.What is the path name for desktop?
I tried to move the file to opt but it seems i cant do it with drag and drop. I think i have to do it from terminal as a root but dont know how to.

Sorry for dumb questions.

---

### Post by honnour on 2010-05-03
my problem is xampp file is on my desktop and i dont know what to write instead of /opt

---

### Post by GuiGuy on 2010-05-03
> **honnour said:**
> my problem is xampp file is on my desktop and i dont know what to write instead of /opt

I suspect /opt is a directory of choice to place the installation files. Try using a directory in your home directory, ie 

mkdir /home/myusername/xampp 

then 

tar xvfz xampp-linux-1.7.3a.tar.gz -C /home/myusername/xampp


But I could be wrong, I often am.

---

### Post by WorMzy on 2010-05-03
I posted this in your other thread, but: can you not just use tasksel (sudo tasksel) to install LAMP?

The problem you're having is that you're not in the right directory to extract the tar. You need to be in the same directory that you downloaded it to. Use cd to change to the download directory (e.g. 'cd Downloads')

---

