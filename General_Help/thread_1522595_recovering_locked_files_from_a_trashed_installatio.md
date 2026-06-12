---
title: "recovering locked files from a trashed installation"
date: 2010-07-02
forum: General Help
---

### Post by duncan303 on 2010-07-02
Hi everyone,

Gosh I have been having problems... Please can somebody help.

I have a laptop that I have been running 64bit lucid on after some problems with NFS Samba and SMB the installation got a bit trashed after some workarounds I removed nautilus completely and rebooted and got the looping login screen........ then I tried a suggestion to purge gdm but that left me with a blank grey screen and a mouse pointer. X11 has failed so I have no graphics

I can login properly to the drive from the terminal and can access my drive contents... I cannot load dolphin or nautilus from the terminal

So I have booted from a live cd and have moved some of my data to another partition but some is locked to the owner (me). How can I get my locked data opened so I can copy or move it to another drive, so I can perform a fresh install.


Many thanks for any help


..

---

### Post by cariboo on 2010-07-02
When you are at the desktop of the Live CD, press Alt-F2 and type:

```
gksu nautilus
```

This will start nautilus as root, and should allow you to retrieve your files.

---

### Post by duncan303 on 2010-07-03
WoW , what a relief...  thanks a million.

the clever dumb balance has been restored!


I also tried it with a 32bit 10.4 live cd  and 64bit 10.4 live cd  and it worked perfectly on my 64bit 10.4 installation. I had to mount the drives first using the livecd desktop and then terminaled

```
gksu nautilus
```then copied the locked data to another partition

cheers again

---

