---
title: "limits of running ubuntu on a usb stick"
date: 2011-09-20
forum: General Help
---

### Post by Havacore on 2011-09-20
I just installed 11.04 on a usb stick, basically to try it out and to have a ubuntu stick incase I ever needed it.  I was wondering about the limits of having it on a stick.  The first thing I ran into was that I could not install google chrome on it.  After that I ran the update manager and I got a warning about being out of space.  After restarting and booting back into windows, I can see that the usb stick still has over 3gb on it.  I used universal usb installer (what ubuntu's site recommends) 

This is more of question of curiosity.  I have a separate partition with 10.04 installed for when I'm doing any serious work.

---

### Post by An Sanct on 2011-09-20
Installed as in LiveUSB? (thats what universal usb installer gives you)

Well, a live USB is a CD image on a thumb drive, with an optional persistance file (casper), so updates are not a good idea here, since the CD is read only. Casper keeps your settings and the /home stuff.

---

### Post by dcstar on 2011-09-20
> **An Sanct said:**
> Installed as in LiveUSB? (thats what universal usb installer gives you)

Well, a live USB is a CD image on a thumb drive, with an optional persistance file (casper), so updates are not a good idea here, since the CD is read only. Casper keeps your settings and the /home stuff.

The "Persistence" file on a Live USB is cumulative write only (a SquashFS limitation, I believe) - this means that you cannot recover the file space from deleting/overwriting files and it will eventually run out of space if you keep writing to it.

This is basically done to spread the write cycles across the whole device rather than risk premature failure by hitting the same area with masses of rewrites (which will eventually kill USB stick drives/SD cards etc.)

You can make the Persistence file big enough to get around this limitation for most circumstances, but you have to be aware of it if you are going to fill it up with updates/big files etc.

---

### Post by An Sanct on 2011-09-20
I agree 100% here with dcstar, but am also aware, that the "universal USB install" for Linux, that was made for windows, will not *install* linux, it will just merely produce a Live USB, so I answered with an "Live USB" answer, rather than a "USB install" one ....

If an actual USB install is wanted, one should have a installation CD ready, install and (IMHO best) no hdd-s plugged in, so there can be no failure, when the GRUB question comes ...

---

