---
title: "Upgrade Dependancies fail"
date: 2009-12-22
forum: General Help
---

### Post by jakr on 2009-12-22
Hi i didn't know where to post this so here seemed the best place:
I'm having a problem with upgrading my ubuntu dependancies which i need to do to install .debs and to use apt-get commands here is the text from terminal:
> jack@home:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libplist0 libusbmux0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libusbmuxd1 usbmuxd
The following NEW packages will be installed
  libusbmuxd1 usbmuxd
0 upgraded, 2 newly installed, 0 to remove and 24 not upgraded.
86 not fully installed or removed.
Need to get 0B/36.9kB of archives.
After this operation, 205kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 206115 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Unpacking usbmuxd (from .../usbmuxd_1.0.1-0ubuntu1~k_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_i386.deb (--unpack):
 trying to overwrite '/usr/sbin/usbmuxd', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb
 /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)does anyone know how to fix this if so can you post it please, 
i'm a bit of a n00b when working out what terminal language means but im alright with some:lolflag: thanks
Jack


EDIT: I fixed this, turns out i had a lot of ipod touch/iphone things that i needed but i used Ubuntu Tweak to clean up packages and now it is fixed

---

### Post by synapsys on 2009-12-22
```
The following packages were automatically installed and are no longer required: libplist0 libusbmux0
**Use 'apt-get autoremove' to remove them.**
The following extra packages will be installed:
  libusbmuxd1 usbmuxd
```.

---

### Post by shak541 on 2010-01-27
hello i too am having this issue.. if i fix it removes rhythmbox.. if i go to install rhythmbox i get the broken packages again
shak@shak-laptop:~$ sudo apt-get install usbmuxd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libusbmuxd1
The following NEW packages will be installed:
  libusbmuxd1 usbmuxd
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/36.9kB of archives.
After this operation, 205kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 153522 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Unpacking usbmuxd (from .../usbmuxd_1.0.1-0ubuntu1~k_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_i386.deb (--unpack):
 trying to overwrite '/usr/sbin/usbmuxd', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb
 /var/cache/apt/archives/usbmuxd_1.0.1-0ubuntu1~k_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
shak@shak-laptop:~$ 

can someone please help.. im stuck in this loop

---

### Post by raktarok on 2010-01-27
Ok this looks like an ugly problem. Try this first:

```
sudo dpkg -l libusbmux0
```

You should get some output indicating that some version of libusbmux0 is installed.

Remove that first.

```
sudo apt-get remove libusbmux0
```

But be careful here, this may try to remove other packages too, and if that happens, note down all the packages that it removes. You will want to install them later again. 

Then try the install commands and see if it works now.

Post any error output you see. Good luck!

---

### Post by Vince N on 2010-02-01
> **raktarok said:**
> Ok this looks like an ugly problem. Try this first:



Having the exact same issue as SHAK however running the commands recommended did NOT help.

---

### Post by raktarok on 2010-02-01
When you try to install usbmuxd after removing libusbmux0 (there is a package of that name right?), does it again try to install libusbmux0? or does it only want to install libusbmuxd1?

Post the exact error you see.

---

### Post by Vince N on 2010-02-01
> **raktarok said:**
> When you try to install usbmuxd after removing libusbmux0 (there is a package of that name right?), does it again try to install libusbmux0? or does it only want to install libusbmuxd1?

Post the exact error you see.

My fault, I was running the dpkg search on usbmuxd which of course did not show as installed.  Running it on libusbmux0 did, Uninstalled and it now works.

---

### Post by raktarok on 2010-02-01
Glad you solved it!

---

### Post by booksnmore4you on 2010-02-14
This is absolutely ridiculously inexcusable incompetence.  Don't these developers try to, er, actually install their upgrades before releasing them? This is exactly the sort of reason why Linux hovers at around 1% of desktop users, and why those of us trying to change that are continually screwed in the a**.

---

### Post by Vince N on 2010-02-14
They probably did.  This error would only occur if you had the other package installed which they may not have.

You get this exact same issue with Windows too you know.  50 Copies of a single DLL which will all load at once and have differences that will cause stuff to blow up in your face.  At least APT is smart enough to tell you up front that this is borked and isn't going to work until you uninstall the other package.

My only real complaint is I think the error could be a little more dumb person readable.

---

### Post by tonycolin on 2010-02-14
I tried the fix you suggest, then I get a "2 broken packages" message.  Running the fix in Synaptic produces:

E: /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb: trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0

Trying to remove libusbmuxd.so.1.0.0 manually (as root) from /usr/lib is not possible either......

---

### Post by raktarok on 2010-02-14
Hi, 

Try these first.

```
sudo dpkg -r libusbmux0 libusbmuxd
```

If you get the broken dependenceies error during this, try these:

```
sudo dpkg --configure --a
sudo apt-get -f install
```

Then try to install **libusbmuxd**
```
sudo apt-get install libusbmuxd1
```

These steps may not serve the problem, so if you see any errors, please post them here. Good luck!

---

### Post by tonycolin on 2010-02-16
Hi Ratarok,

Thanks, that fixed it.  FWIW dpkg doesn't like your "--a" option, so I substituted "-a"

I need to read up the MAN on --configure obviously!

---

