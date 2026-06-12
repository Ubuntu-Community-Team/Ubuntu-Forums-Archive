---
title: "Boot problem"
date: 2009-11-15
forum: General Help
---

### Post by ((sbi.23)) on 2009-11-15
Alright, so here is the situation.

I just wiped my computer and installed Ubuntu 9.10 yesterday.

Everything was going fine and i was starting to get the hang of it, but im still a noob to any linux software, as im coming from a pc world.

I dont know if this had anything but i typed in a command in the terminal and it froze the computer and forced restarted itself.

Now when trying to boot up it says:

"intel UNDI, PXE-2.0 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL8139(X)/8130/810X PCI Fast Ethernet Controller v.2.13 (020326)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM."

Nothing is plugged into the laptop except the power cord
The message just flashes over and over.
I dont know if this is caused by me messing with the terminal in Ubuntu, or if its just a hardware problem, since this laptop is quite old. 

Any ideas?

---

### Post by dcstar on 2009-11-15
> **((sbi.23)) said:**
> Alright, so here is the situation.

I just wiped my computer and installed Ubuntu 9.10 yesterday.

Everything was going fine and i was starting to get the hang of it, but im still a noob to any linux software, as im coming from a pc world.

I dont know if this had anything but i typed in a command in the terminal and it froze the computer and forced restarted itself.

Now when trying to boot up it says:

"intel UNDI, PXE-2.0 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL8139(X)/8130/810X PCI Fast Ethernet Controller v.2.13 (020326)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM."

Nothing is plugged into the laptop except the power cord
The message just flashes over and over.
I dont know if this is caused by me messing with the terminal in Ubuntu, or if its just a hardware problem, since this laptop is quite old. 

Any ideas?

The system is no longer booting off the hard drive, either the BIOS has been changed or something happened to kill the Ubuntu installation (or the hard drive died).

Boot off the Ubuntu CD and try to repair Grub (do a search for detailed instructions).

---

### Post by wulfgang on 2009-11-15
I had that problem in 9.04. See if this helps. It seems alot of people have this problem:
[http://www.geekstogo.com/forum/PXE-E61-Media-Test-Failed-Check-cable-t54244.html](http://www.geekstogo.com/forum/PXE-E61-Media-Test-Failed-Check-cable-t54244.html)

Also, make sure in your boot order that "network" or "ethernet" is selected because that will cause that error also.(It did for me.)

---

### Post by ranch hand on 2009-11-15
It might be good to say what this command was.

Assuming that this is boot problem;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by ((sbi.23)) on 2009-11-15
Hmm, i didnt notice this befor, but when i booted from the LiveCD to try and  fix/recover Grub i spotted something. The SMART Data icon on top of the screen pointed out to me that my disk may are failing. 

So i looked at more info and the Disk has 151 bad sectors...

So yea im guessing that the HDD just reached the end of its life, so im just going to buy a new one, hopefully then everything will work normally.

Thanx

---

