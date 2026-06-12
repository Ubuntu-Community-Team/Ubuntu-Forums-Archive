---
title: "Problems mounting USB hard drives"
date: 2009-06-26
forum: General Help
---

### Post by jrz on 2009-06-26
Since updating to Ubuntu 9.04 I've been having great difficulty getting USB drives to mount or remain mounted. I have 10 external drives, all of which mounted reliably previously and the ones which remain ntfs formatted will still mount reliably in WinXP, but none are reliable in Ubuntu, including the few I've reformatted to ext3.

I experience the same problem using three different computers, an old IBM Thinkpad R40 notebook, a much newer Compaq Presario A900 notebook, and an new dual CPU HP Pavilion G8635l desktop computer.

The most used computer, the desktop, now shows /dev to contain entries for sda, along with it's numbered partitions which relate to the internal drive, and I notice that the external drives now try to mount and fail using sdf, and there exists entries in /dev for sdb, sdc, sdd, and sde which remain after shutting down and rebooting. 

Sometimes I am able to successfully mount a USB drive by moving from one usb port to another, but don't suspect the port as the same situation exists on 3 different computers, but not if booted to Win XP where all usb ports work reliably.

Recently the problem appears to have worsened, and I also notice that there have been a number of updates related to the hal package which I've come to suspect as one possible source of the problem. 

This problem only exists trying to mount usb hard drives, while memory sticks mount and work reliably consistently.

Are any others experiencing a similar problem?

---

### Post by Kaiva Azure on 2009-07-29
Hi, I am having the same (or similar) issues but its with USB anything.
After installing 9.04 over my old 7.04 USB was working fine and things were awesome. I went about my business installing upgrades and whatnot to have MP3 functionality since my collection of music is mp3 (converting to FLAC would be retarded as its impossible to GAIN quality) anywho. while doing the same on another machine I came back to mine to look for more upgrades and found that my USB stick had unmounted for some unknown reason. the other machine has not had this problem yet but I suspect that installing the upgrades will do the same there as well.

note: my usb stick works fine on windows (same machine, I dual boot) ubuntu just suddenly no longer auto-mounts the usb stick and I have found no understandable method to manually mount the stick.

---

### Post by jrz on 2009-07-31
I've been applying updates as they become available, hoping that one of them might contain a fix for the problem, but find the problem only gets worse so I've stopped trying to mount external drives. Sadly, I've reformatted most of my external drives to ext3 so they are no longer accessable under WinXP, leaving what files I had been able to store on them inaccessable, and the last attempt has left one 500 GB drive containing over 200 GB of data corrupted in a way that it will no longer mount at all. At the moment I have an NAS drive which I can save files to via a LAN transfer, but am quickly running out of space while I have about 4 TB of space on external drives which I can not make use of.

---

### Post by Kaiva Azure on 2009-07-31
that's horrible, I hope someone can deliver a fix for you, i just gave up on Linux altogether, it just killed a 40gb drive i had it on and i could do nothing to restore it, my system cant even see it anymore.

I would like to use ubuntu but, this is just worse than windows for me :(

I'll still be subscribed to this thread juuust in case there's a great easy fix for all the hell the both of us have endured. till then I'm sticking with my Windblows XP SP3 pirate edition. at least its not killing my hard drives. O_o

---

