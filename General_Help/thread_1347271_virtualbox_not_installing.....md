---
title: "virtualbox not installing...."
date: 2009-12-06
forum: General Help
---

### Post by muctadir on 2009-12-06
first i installed 32 bit virtualbox on my 64 bit system using force architecture command. but it does not work. then i tried to install virtualbox 64 bit. but below messages are shown-
 p, li { white-space: pre-wrap; }  [FONT=Monospace]Selecting previously deselected package libcurl3.[/FONT]
 [FONT=Monospace](Reading database ... (Reading database ... 5%(Reading database ... 10%(Reading database ... 15%(Reading database ... 20%(Reading database ... 25%(Reading database ... 30%(Reading database ... 35%(Reading database ... 40%(Reading database ... 45%(Reading database ... 50%(Reading database ... 55%(Reading database ... 60%(Reading database ... 65%(Reading database ... 70%(Reading database ... 75%(Reading database ... 80%(Reading database ... 85%[/FONT]
 [FONT=Monospace]dpkg: warning: files list file for package `virtualbox-3.0' missing, assuming package has no files currently installed.[/FONT]
 [FONT=Monospace](Reading database ... 90%(Reading database ... 95%(Reading database ... 100%(Reading database ... 104906 files and directories currently installed.)[/FONT]
 [FONT=Monospace]Unpacking libcurl3 (from .../libcurl3_7.19.5-1ubuntu2_amd64.deb) ...[/FONT]
 [FONT=Monospace]Setting up libcurl3 (7.19.5-1ubuntu2) ...[/FONT]
 [FONT=Monospace][/FONT]
 [FONT=Monospace]Processing triggers for libc-bin ...[/FONT]
 [FONT=Monospace]ldconfig deferred processing now taking place[/FONT]
 [FONT=Monospace]dpkg: regarding .../virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_amd64.deb containing virtualbox-3.1:[/FONT]
 [FONT=Monospace] virtualbox-3.1 conflicts with virtualbox[/FONT]
 [FONT=Monospace]  virtualbox-3.0 provides virtualbox and is present and unpacked but not configured.[/FONT]
 [FONT=Monospace]dpkg: error processing /home/dinar/virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_amd64.deb (--install):[/FONT]
 [FONT=Monospace] conflicting packages - not installing virtualbox-3.1[/FONT]
 [FONT=Monospace]Errors were encountered while processing:[/FONT]
 [FONT=Monospace] /home/dinar/virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_amd64.deb[/FONT]

[FONT=Monospace][/FONT]
[FONT=Monospace]i am actually installing from deb files............[/FONT]

[FONT=Monospace][/FONT]
[FONT=Monospace]please help me solving ts problem...
[/FONT]
 [FONT=Monospace][/FONT]

---

### Post by MelDJ on 2009-12-06
edit. 
where did you get the .deb package from? is it [http://www.virtualbox.org/wiki/Linux_Downloads?](http://www.virtualbox.org/wiki/Linux_Downloads?)

---

### Post by muctadir on 2009-12-06
actually i downloaded the deb. and at the time of installing the error occurred.......

---

### Post by MelDJ on 2009-12-06
do you have virtualbox3.0 installed? if so try uninstalling it then install 3.1.
if you have nothing important in 3.0

---

### Post by muctadir on 2009-12-06
i tried several commands to remove virtualbox-
sudo apt-get remove virtualbox
sudo apt-get remove --purge virtualbox
sudo dpkg -r VirtualBox

but they can't find virtualbox installed. then i tried the KPackageKit to find and remove that. but i could not find that.

after that i searched for virtualbox and deleted all files related to virtualbox.
then i tried to install virtualbox 64 bit. but the same error occurred.

---

### Post by muctadir on 2009-12-06
please i need some help here.......

---

### Post by plucky on 2009-12-06
> **muctadir said:**
> i tried several commands to remove virtualbox-
sudo apt-get remove virtualbox
sudo apt-get remove --purge virtualbox
sudo dpkg -r VirtualBox

but they can't find virtualbox installed. then i tried the KPackageKit to find and remove that. but i could not find that.

after that i searched for virtualbox and deleted all files related to virtualbox.
then i tried to install virtualbox 64 bit. but the same error occurred.

Open a terminal and ```
dpkg --get-selections | grep virtualbox
``` to find out what version is installed.

Then ```
sudo apt-get remove --purge virtualbox-3.0
``` if it is version 3.0.

Why not use synaptic package manager if the CLI is not working for you?

Good Luck

---

### Post by afselby1 on 2009-12-14
muctadir,

I am having the same problem.  Did you solve it?

thanks
[U]  
[/U]

---

### Post by Rob_H on 2009-12-14
> **muctadir said:**
> 
 [FONT=Monospace] virtualbox-3.1 conflicts with virtualbox[/FONT]
 [FONT=Monospace]  virtualbox-3.0 provides virtualbox and is present and unpacked but not configured.[/FONT]


Sounds like your package database is in a funky state. Try:

```
sudo apt-get -f install
```

---

### Post by dqqdrake on 2010-06-15
Had the same problem with upgrading 3.1 to 3.2.
*sudo apt-get remove --purge virtualbox-3.1*
worked for me.

---

### Post by mrcottonmouth on 2010-06-16
Removing and purging it, didn't mess up your virtual machines?

---

