---
title: "GRUB error 12"
date: 2009-07-28
forum: General Help
---

### Post by JIMIneitor on 2009-07-28
Hi there!

a few minutes ago, i was in the means of rezising my windows partition, and since i dont have any live cd available, i deleted my home partition of linux (172 GB), thinking that linux would just drop me to a prompt.

Well, i made it to a stable (not failsafe) Gnome session, logged as root, but i also noticed that whenever i try to boot Windows, GRUB tells me "Error 12 Device not found" or something like that.


I made it to log in as root, so not everything is lost

Right now im using Gparted to enlarge my windows partition!

---

### Post by philcamlin on 2009-07-28
I had the similar problem. Here is the fix.... load your "original" windows cd (I was using XP Pro) and boot your computer. After the cd loads, go to Recovery Console and type fixmbr followed by fixboot. 

IMPORTANT: This will only help you log on to your XP partition if you need to save any important files. The above commands re-writes the Master Boot Recorder and thus you will have to reinstall grub and hope you don't get the same error message:popcorn:

---

### Post by JIMIneitor on 2009-07-28
isnt there a way to modify grub's menu.lst or grub.conf and thus fixing these?

---

### Post by philcamlin on 2009-07-28
> **JIMIneitor said:**
> isnt there a way to modify grub's menu.lst or grub.conf and thus fixing these?

you have to do that :P
or xp wont see the light of day again :O

---

### Post by JIMIneitor on 2009-07-28
but XP (in my case Vista) noesnt have the MBR, the MBR is in the sector 0 of the hard drive, and it isnt corrupt, i think, because it lets me get to grub

---

### Post by philcamlin on 2009-07-28
it still needs to get to vista mbr tells vista where to boot from etc... 
so try the way i posted above and see if it works :):popcorn:

good luck

---

### Post by JIMIneitor on 2009-07-28
damn, ill have to wait a week to get to that cd! :(:(:(:(

---

### Post by philcamlin on 2009-07-28
ah thats a bummer :(

ill come back in a week and tell me what your outcome is :popcorn:

---

### Post by JIMIneitor on 2009-07-28
ok, ill do, enjoy your popcorn!:KS

---

