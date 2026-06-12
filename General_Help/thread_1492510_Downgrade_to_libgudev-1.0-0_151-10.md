---
title: "Downgrade to libgudev-1.0-0_151-10 ??"
date: 2010-05-24
forum: General Help
---

### Post by alejandro.mc on 2010-05-24
Hi, apparently there's an issue with cdrom/dvdrom drives in certain occasions. I have that issue, if you want to read about it:

[https://bugs.launchpad.net/ubuntu/+bug/554433](https://bugs.launchpad.net/ubuntu/+bug/554433)

So I read there about a guy that downgraded this packages:

libgudev-1.0-0_151-10
libudev0_151-10
udev_151-10

from the 151-12 version that I currently have in my Ubuntu 10.04 LTS, that is not working properly and doesn't allow me to mount cdrom0, and that solved the issue for him and some other guys..

I'm kind of a noob, so I downloaded the packages, they are .deb, but when I double click and try to install, the "Install" button is greyed out because it says there is already a newer version of the file installed.

Couple of questions:

1. How can I install them (downgrade them..)?

2. If using Synaptic to uninstall the newer version, apparently a lot of software has to be uninstalled (brasero, empathy, evolution, and the list goes on), is there a way to avoid this? I don't want to lose, not even temporarily those programs, not to mention their configuration, that took me a couple of days..

Thanks a lot,

Alejandro
Buenos Aires
Argentina

---

### Post by Bobhuber on 2010-05-24
> **alejandro.mc said:**
> Hi, apparently there's an issue with cdrom/dvdrom drives in certain occasions. I have that issue, if you want to read about it:

[https://bugs.launchpad.net/ubuntu/+bug/554433](https://bugs.launchpad.net/ubuntu/+bug/554433)

So I read there about a guy that downgraded this packages:

libgudev-1.0-0_151-10
libudev0_151-10
udev_151-10

from the 151-12 version that I currently have in my Ubuntu 10.04 LTS, that is not working properly and doesn't allow me to mount cdrom0, and that solved the issue for him and some other guys..

I'm kind of a noob, so I downloaded the packages, they are .deb, but when I double click and try to install, the "Install" button is greyed out because it says there is already a newer version of the file installed.

Couple of questions:

1. How can I install them (downgrade them..)?

2. If using Synaptic to uninstall the newer version, apparently a lot of software has to be uninstalled (brasero, empathy, evolution, and the list goes on), is there a way to avoid this? I don't want to lose, not even temporarily those programs, not to mention their configuration, that took me a couple of days..

Thanks a lot,

Alejandro
Buenos Aires
Argentina
It's not just Lucid.I run dual boot with Karmic on a separate partition with the same problem.By same problem I mean using DVD/RW disks that I have tried to blank and write to.Brasero wont see them and I can't mount them. Install GnomeBaker CD/DVD writer and you will be able write to your DVD/RW disks. Don't ask me why because I have no clue other than the program looks at the disk differently before attempting to write to it.

---

### Post by alejandro.mc on 2010-05-24
Yep I know, but apparently downgrading to libgudev-1.0-0_151-10,etc..the three packages, solves the mounting COMPLETELY, so I'm trying to get my hands on the three .deb, but they are nowhere to be found, so I'll try to prepare them, but how?? Some guy downloaded an alternate version of ubuntu and extract them..I wouldn't know how to do that..

Any ideas??

Thanks!

NOPE I just tried and the problem is still there..I tried several udev and libraries versions and the problem remains..I could really use a hand with this..

---

