---
title: "Karmic 9.10 - Boot Errors"
date: 2010-01-25
forum: General Help
---

### Post by bbqau on 2010-01-25
Hello, 

Running Ubuntu 9.10 Karmic on my home server (specs below), and have been experiencing various problems over the past few months. Early on in the piece i was getting sector failure, i used fdisk and fixed them only to have them return once again. So i downloaded my hard drive manufacturers mid level formatting tool and ran it on the disk from my windows / ubuntu desktop ( of which i have no problems running ) then reinstalled the OS on my server.

It had been running fine for a month or so and all of a sudden this morning when i rebooted it ran weird.

Firstly it would not boot ubuntu and just hung for around 20 minutes on the loading screen ( with ubuntu tile in center). So i rebooted it manually, it then loaded, only to randomly loose the desktop menu's and all ability to control the server. At this time i attempted to SSH into the machine with no success, indiciating that it was not simply a Gnome desktop failure but rather something lower level.

I manually rebooted the server once again only to receive the following error.

```
error: biosdisk read error
   Failed to boot default entries

Press any key to continue...
```

I found out that there is a bug on launchpad for this [here](https://launchpad.net/bugs/396564) however as of yet i don't think anyone really knows whats causing it.

Below are the server specs
**cpu**  : AMD X2 4200+
**mobo** : ASUS M2N-SLi-Deluxe
**ram**  : Geil PC6400 (800Mhz)
**hdd**  : Samsung 500GB SATAII (16M)

Any other information required i will attempt to ascertain.

****edit****
I may have a temporary solution :: post #43 ~ [here](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/396564)
> I don't know if this is a solution for those of you who run RAID, however for me i just run a single Hard Drive so it appears to have worked.

I disabled my non existent Floppy Drive in the BIOS as per Stephens workaround, i went a few steps further and configured my bios settings.

I disabled all options to utilise RAID and made sure my HDD was connected to SATA I ( I have 6 HDD spots ~ consult your Motherboard Manual or get a magnifying glass out to read it on the mobo ) and i no longer have the problems.

I hope this is how simple the solution is for users like me, i will report back with the stability of this process and let people know if it is sustainable.

---

