---
title: "i need help"
date: 2011-08-06
forum: General Help
---

### Post by mpvick on 2011-08-06
i have ubuntu 11.04 ihave tried 
mpvick@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-  

but it didnt work i am using a direct connection but it said it could not find b43  also i am dual booting between windows 7 starter and ubuntu 11.04  and this is my firtst time using linux also i am in 9th grade so i probably need it in walk through format i have a brodcom 208.11 card and im running it on the hp mini 110 and i downloaded strait from ubuntu.com so no disc or usb any way like i said the wirless says that i am missing firmware please help.

---

### Post by karlson on 2011-08-06
> **mpvick said:**
> i have ubuntu 11.04 ihave tried 
mpvick@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-  

but it didnt work i am using a direct connection but it said it could not find b43  also i am dual booting between windows 7 starter and ubuntu 11.04  and this is my firtst time using linux also i am in 9th grade so i probably need it in walk through format i have a brodcom 208.11 card and im running it on the hp mini 110 and i downloaded strait from ubuntu.com so no disc or usb any way like i said the wirless says that i am missing firmware please help.

run:
```

sudo aptitude

```

Then search for b43.  I don't think the firmware-b43 package exists, but you can check in aptitude.

---

### Post by daccount10 on 2011-08-06
It should work. Make sure you have the correct package name. You could also try doing it in synaptic if you can't figure out.

This is also a shorter way to install 2+ packages:
```
sudo apt-get install foo bar
```

---

### Post by mpvick on 2011-08-06
it didn't work it said not found and icopyed and pasted it

---

### Post by doc_cypher on 2011-08-06
Just one observation. I don't really know what these packages are for but I just checked that the last package is actually called "firmware-b43-lpphy-installer". Is there a typo in the post. If this is what you are actually running, then I think ubuntu should indeed complain.

---

### Post by mpvick on 2011-08-06
it still said file not found
it said package foo not found and package bar not found

---

### Post by doc_cypher on 2011-08-06
Can you run this and post the output here:

```

sudo apt-get -s install b43-fwcutter firmware-b43-lpphy-installer

```

---

### Post by daccount10 on 2011-08-06
try
```
sudo apt-get install firmware-b43-lpphy-installer  b43-fwcutter
```
or
find it in synaptic where you can find the right package easily

---

### Post by wildmanne39 on 2011-08-06
Hi, that is the same command I gave him in the networking thread.

Like I posted over there you did the command wrong you just need to copy and paste it.
Thank you

---

### Post by jramshu on 2011-08-06
Edit: Nevermind wildmanne39 is already helping.

---

### Post by mpvick on 2011-08-06
how do i get to synaptic

---

### Post by mpvick on 2011-08-06
i did but it isnt working the problem is im not sure why but it says that its unable to locate

---

### Post by mpvick on 2011-08-06
mpvick@ubuntu:~$ sudo apt-get install firmware-b43-lpphy-installer b43-fwcutter
[sudo] password for mpvick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer
E: Unable to locate package b43-fwcutter
mpvick@ubuntu:~$ sudo apt-get install firmware-b43-lpphy-installer  b43-fwcutterReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer
E: Unable to locate package b43-fwcutter
mpvick@ubuntu:~$ sudo apt-get install firmware-b43-lpphy-installer  b43-fwcutterReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer
E: Unable to locate package b43-fwcutter
mpvick@ubuntu:~$

---

### Post by jramshu on 2011-08-06
Maybe he doesn't have the repository enabled? 


Just a thought.

---

### Post by wildmanne39 on 2011-08-06
Hi,click on the power button in the top right corner of the screen then click on system settings, in the window that opens scroll down to system, then click on synaptic package manager, then click on settings, repositories, then put a check by multiverse then close synaptic.

Then run this command
```
sudo apt-get update && sudo apt-get upgrade
```
it will take a while to install the updates, it may require a restart.

Then run the commands to install the driver and firmware again.
Thank you

---

### Post by sinbowden on 2011-08-06
Binary package hint: b43-fwcutter
 Do not install
 ProblemType: Package
DistroRelease: Ubuntu 11.04
Package: firmware-b43-lpphy-installer 4.174.64.19-5
ProcVersionSignature: Ubuntu 2.6.35-28.50-generic 2.6.35.11
Uname: Linux 2.6.35-28-generic i686
NonfreeKernelModules: wl
Architecture: i386
Date: Sat Jun 11 21:09:37 2011
ErrorMessage: ErrorMessage: il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 4
InstallationMedia: Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
PackageArchitecture: all
SourcePackage: b43-fwcutter
Title: package firmware-b43-lpphy-installer 4.174.64.19-5  failed to install/upgrade: ErrorMessage: il sottoprocesso vecchio script  di post-installation ha restituito lo stato di errore 4
UpgradeStatus: Upgraded to natty on 2011-06-11 (0 days ago)

---

### Post by sinbowden on 2011-08-06
this thread might help! [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by wildmanne39 on 2011-08-06
He PM me and it is working now.

---

### Post by sinbowden on 2011-08-06
> **wildmanne39 said:**
> He PM me and it is working now.
cool :)

---

### Post by jramshu on 2011-08-07
> **wildmanne39 said:**
> He PM me and it is working now.

What did he do to fix it?

---

### Post by wildmanne39 on 2011-08-07
Hi, after he run 
```
sudo apt-get update && sudo apt-get upgrade
```
Then he ran the command in the previous post to install the driver and firmware.

---

