---
title: "Installing Pacman"
date: 2010-04-11
forum: General Help
---

### Post by uRock on 2010-04-11
I am having problems installing Pacman on my daughter's Karmic system. 

Here is the output of the attempted install;```
sarah@no-windows:~$ sudo apt-get install pacman
[sudo] password for sarah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pacman
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.7kB of archives.
After this operation, 164kB of additional disk space will be used.
(Reading database ... 156384 files and directories currently installed.)
Unpacking pacman (from .../pacman_10-17ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/pacman_10-17ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/man/man6/pacman.6.gz', which is also in package xscreensaver-data-extra 0:5.08-0ubuntu5
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/pacman_10-17ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can someone tell me what to tr next in order to get it installed?

Thanx,
Ronnie

---

### Post by uRock on 2010-04-12
I called Mr.Bump to see if he could help.

---

### Post by blueridgedog on 2010-04-12
The only error I see is:

trying to overwrite '/usr/share/man/man6/pacman.6.gz', which is also in package xscreensaver-data-extra 0:5.08-0ubuntu5

You could move this file temporarily, 

```
sudo mv /usr/share/man/man6/pacman.6.gz /home/sarah/
```

Then run the install command again.  I doubt you will ever need the man page for the pacman screen saver...but you never know!

---

### Post by uRock on 2010-04-12
> **blueridgedog said:**
> The only error I see is:

trying to overwrite '/usr/share/man/man6/pacman.6.gz', which is also in package xscreensaver-data-extra 0:5.08-0ubuntu5

You could move this file temporarily, 

```
sudo mv /usr/share/man/man6/pacman.6.gz /home/sarah/
```Then run the install command again.  I doubt you will ever need the man page for the pacman screen saver...but you never know!

Lol, If I am reading that man page, then life is in fact too boring. Thanks for the idea, I'll try it in a few.

Thanx,
Ronnie

---

### Post by uRock on 2010-04-12
I ended up removing that screensaver package to make it work.

---

