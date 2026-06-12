---
title: "Flash/Chrome Help"
date: 2010-06-24
forum: General Help
---

### Post by jschille on 2010-06-24
Hello!

I have not had flash working on firefox, but just downloaded chrome and flash is still not working.

As an example, when i visit youtube.com it states:
   "You need to upgrade your adobe flash player. Please click to download"

I then go to the adobe site, click on the .deb for Ubuntu and then it says "Wrong architecture i386." Doesn't even say it supports chrome, have i done something seriously thing?

Edit: I have a 64bit OS

---

### Post by maizuddin35 on 2010-06-24
have you already install any flash plugin for ubuntu.?

---

### Post by jschille on 2010-06-24
> **maizuddin35 said:**
> have you already install any flash plugin for ubuntu.?

I think I may have deleted it... haha
so new to this

Edit: just went to Synaptic Package manager and attempted to install the plugins, got this error message.

E: flashplugin-installer: subprocess installed post-installation script returned error exit status 1
E: flashplugin-nonfree: dependency problems - leaving unconfigured
It is marked as installed now though.... still can't view flash vidoes though

Edit: Another error message... After running the command to install ubuntu-restricted-extras. I get...
```
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by maizuddin35 on 2010-06-24
try this :
[B]sudo aptitude purge adobe-flashplugin
sudo aptitude install adobe-flashplugin
[/B]

---

### Post by jschille on 2010-06-24
> **maizuddin35 said:**
> try this :
[B]sudo aptitude purge adobe-flashplugin
sudo aptitude install adobe-flashplugin
[/B]

my output

```


jb@jb-laptop:~$ sudo aptitude install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for adobe-flashplugin
No candidate version found for adobe-flashplugin
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by maizuddin35 on 2010-06-24
that kinda wierd thing, there is no package?

---

### Post by slooksterpsv on 2010-06-24
> **maizuddin35 said:**
> try this :
[B]sudo aptitude purge adobe-flashplugin
sudo aptitude install adobe-flashplugin
[/B]

Try this instead - according to the logs your posted above it's having trouble with: flashplugin-installer - so try these
```

sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-installer

```

What does that do for you? I'm running 64-bit Ubuntu and have Google Chrome running really well with Youtube/Flash. Actually that's how I'm typing this post, so it does work for sure.

---

### Post by maizuddin35 on 2010-06-24
that thing install back the installer?

---

### Post by slooksterpsv on 2010-06-24
You know... now that I think of it... lemme check something...

I don't know if I actually installed it from Software Center, I think I went to Adobe.com and installed the DEB from there directly. Try that instead, well run:

sudo apt-get remove flashplugin-installer

Then go to adobe.com and download and install the deb package.

---

### Post by lovinglinux on 2010-06-25
Do this:

> **3hough said:**
> Fixed! Thanks for the pointer. In case anyone else hits this error, the solution was to

[LIST=1]
[*]Disable the partner repository
[*]```
sudo apt-get purge nspluginwrapper
```
[*]```
sudo apt-get autoremove
```
[*]Reinstall the dozen or so packages that nspluginwrapper depends on directly. Find the list by running ```
apt-cache depends nspluginwrapper
```
[*]Run FLASH-AID if you're using Firefox, or
```
sudo apt-get install flashplugin-installer
```
[/LIST]

---

