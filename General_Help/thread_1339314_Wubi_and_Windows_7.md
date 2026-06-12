---
title: "Wubi and Windows 7"
date: 2009-11-27
forum: General Help
---

### Post by FreakShow! on 2009-11-27
Hi guys,

I'm trying to install Ubuntu via Wubi through Windows 7, but the install doesn't edit the bootmanager.

I've googled already and tried it in Vista compatibility mode, but that doesn't work either.

I've installed EasyBCD and have been trying to add the bootloader myself, but I am not 100% sure of what I'm doing. I added a Wubi option which installed NeoGrub, which points to a menu.lst in the
C:\Device\HarddiskVolume1\NST folder, which in turn points to a menu.lst in the 
find --set-root --ignore-floppies \ubuntu\winboot\menu.lst
configfile \ubuntu\winboot\menu.lst

which doesn't exist. I've thought about creating one, but I don't know what's meant to be in that.

TIA for any help :)

---

### Post by HellHornet on 2009-11-27
not a good idea to use Wubi , read some of the problems people have been having (inc me)

Better to do a fresh install on a separate partition.
Hellhornet

---

### Post by FreakShow! on 2009-11-27
It's on a laptop, small HDD so Wubi is favourable to utilise the maximum HDD space possible. If I have to start playing with partitions I'm going to run out of room.

I've managed to fix it sort of though.

Renamed original Ubuntu folder to Ubuntu.old (just so it's not overwritten and Wubi doesn't find it).

Next install a fresh copy of Wubi (doesn't need to be in compatibility mode)

Copy the wubildr and wubildr.mbr from:
C:\ubuntu\winboot
and place it in C:\

Then open a cmd prompt in administrator mode.
Create a new BCD entry, jot down the ID and point it to the wubildr.mbr file in C:\

It then boots and installs a new Ubuntu. You can then mount the original disks in Ubuntu and copy across the contents of the /home folder to get all your old settings back :)

---

