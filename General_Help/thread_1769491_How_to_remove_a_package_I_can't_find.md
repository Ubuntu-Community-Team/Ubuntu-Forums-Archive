---
title: "How to remove a package I can't find?"
date: 2011-05-28
forum: General Help
---

### Post by AliceKingsley on 2011-05-28
So, I messed up. I couldn't find an amd64 version of the package I wanted, so I forced the architecture on the i386 version I found. (The package in question is xinput-calibrator, so that I can finally get my touchscreen to work.) I later found and added the repository that has the 64 version and tried to install it. It won't install the 64 version because I already have the i386 version. But it also won't let me remove the i386 version. 
```
alicekingsley@CheshireCat:~$ sudo apt-get install xinput-calibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xinput-calibrator
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/38.2 kB of archives.
After this operation, 184 kB of additional disk space will be used.
dpkg: error processing /var/cache/apt/archives/xinput-calibrator_0.7.5-0ubuntu1_amd64.deb (--unpack):
 xinput-calibrator: 0.7.5-0ubuntu1 (Multi-Arch: no) is not co-installable with xinput-calibrator:i386 0.7.5-1ubuntu1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/xinput-calibrator_0.7.5-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Here are the ways I've tried to remove it:
```
alicekingsley@CheshireCat:~$ sudo apt-get remove xinput-calibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xinput-calibrator is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```
```
alicekingsley@CheshireCat:~$ sudo apt-get remove xinput-calibrator:i386
E: Unable to locate package xinput-calibrator:i386
```
```
alicekingsley@CheshireCat:~$ sudo apt-get remove xinput-calibrator:i386 0.7.5-1ubuntu1
E: Unable to locate package xinput-calibrator:i386
E: Unable to locate package 0.7.5-1ubuntu1
E: Couldn't find any package by regex '0.7.5-1ubuntu1'
```
```
alicekingsley@CheshireCat:~$ sudo apt-get remove "xinput-calibrator:i386 0.7.5-1ubuntu1"
E: Unable to locate package xinput-calibrator:i386 0.7.5-1ubuntu1
E: Couldn't find any package by regex 'xinput-calibrator:i386 0.7.5-1ubuntu1'
```
Sorry for the wall of code, I'm new enough that I don't know what you'd need to know to help. There has to be a way to find 'xinput-calibrator:i386 0.7.5-1ubuntu1' to remove it, but I have no idea how. Please help.

---

### Post by linuxinstalledfromhdd on 2011-05-28
Have you tried to locate the package with Synaptic Package Manager? 

From the terminal:

sudo synaptic

---

### Post by wildmanne39 on 2011-05-28
> **AliceKingsley said:**
> So, I messed up. I couldn't find an amd64 version of the package I wanted, so I forced the architecture on the i386 version I found. (The package in question is xinput-calibrator, so that I can finally get my touchscreen to work.) I later found and added the repository that has the 64 version and tried to install it. It won't install the 64 version because I already have the i386 version. But it also won't let me remove the i386 version. 
```
alicekingsley@CheshireCat:~$ sudo apt-get install xinput-calibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xinput-calibrator
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/38.2 kB of archives.
After this operation, 184 kB of additional disk space will be used.
dpkg: error processing /var/cache/apt/archives/xinput-calibrator_0.7.5-0ubuntu1_amd64.deb (--unpack):
 xinput-calibrator: 0.7.5-0ubuntu1 (Multi-Arch: no) is not co-installable with xinput-calibrator:i386 0.7.5-1ubuntu1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/xinput-calibrator_0.7.5-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Here are the ways I've tried to remove it:
```
alicekingsley@CheshireCat:~$ sudo apt-get remove xinput-calibrator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xinput-calibrator is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

```
```
alicekingsley@CheshireCat:~$ sudo apt-get remove xinput-calibrator:i386
E: Unable to locate package xinput-calibrator:i386
```
```
alicekingsley@CheshireCat:~$ sudo apt-get remove xinput-calibrator:i386 0.7.5-1ubuntu1
E: Unable to locate package xinput-calibrator:i386
E: Unable to locate package 0.7.5-1ubuntu1
E: Couldn't find any package by regex '0.7.5-1ubuntu1'
```
```
alicekingsley@CheshireCat:~$ sudo apt-get remove "xinput-calibrator:i386 0.7.5-1ubuntu1"
E: Unable to locate package xinput-calibrator:i386 0.7.5-1ubuntu1
E: Couldn't find any package by regex 'xinput-calibrator:i386 0.7.5-1ubuntu1'
```
Sorry for the wall of code, I'm new enough that I don't know what you'd need to know to help. There has to be a way to find 'xinput-calibrator:i386 0.7.5-1ubuntu1' to remove it, but I have no idea how. Please help.
Hi, as long as you know the name you can use
```
sudo apt-get --purge remove packagename
```

---

### Post by Pand5461 on 2011-05-28
```
sudo dpkg -r package-name
``` worked fine to me in a similar case.

---

### Post by oldos2er on 2011-05-28
Clear the cache ```
sudo apt-get clean
``` Then retry ```
sudo apt-get install xinput-calibrator
```

---

### Post by AliceKingsley on 2011-05-28
I think I must have phrased the problem poorly, so let me try again: 

When I try to install package A, I get an error that I can't because it's incompatible with package B that I already have installed. 

When I try to remove package B, I get an error that there's nothing installed by that name. 

I have a 64-bit system. Package A is the 64-bit *xinput-calibrator: 0.7.5-0ubuntu1*, which I want. Package B is the 32-bit *xinput-calibrator:i386 0.7.5-1ubuntu1*, which I force-installed when I couldn't find package A. (I'd assumed there wasn't a 64-bit version, and I've had to do that with a lot of 32-bit packages, without issue until now.) When I type *xinput-calibrator*, it assumes I mean package A, so I don't know how to find package B to remove it. 

I've tried calling it *xinput-calibrator:i386*, and it's unable to locate a package by that name. I tried *xinput-calibrator:i386 0.7.5-1ubuntu1*, and because of the spaces it looks for two different packages. I tried *"xinput-calibrator:i386 0.7.5-1ubuntu1"*, and it again can't find a package by that name. 

I've also tried finding it with both the Ubuntu Software Center and Synaptic, and they both come up with the uninstalled 64-bit package only.

Edited to add: 
I can find and run the 32-bit package, it shows up as Calibrate Touchscreen in Unity's launcher. Here's the error I get when I run it: ```
xinput_calibrator: error while loading shared libraries: libgtkmm-2.4.so.1: wrong ELF class: ELFCLASS64
``` Because of this, I also tried calling it *xinput_calibrator*, which it can't find.

---

