---
title: "BIOS unlock help"
date: 2010-05-07
forum: General Help
---

### Post by Svarta Draken on 2010-05-07
Hey, I recently was given a Dell Inspiron 6000 laptop which was having some problems booting up in Windows XP and began to attempt to fix it. The only solution I tried which actually worked was reformatting the hard drive and installing Linux on the machine. I installed Ubuntu Lucid v10.04. Things have been going great since then, however I just encountered a problem which I can't solve with my limited knowledge.

I want to boot from a CD-ROM I just got, however the BIOS is set so that it boots from the hard drive first, bringing up Ubuntu. When I tried to change this setting in the BIOS menu, I discovered that the BIOS has been password protected. I called the guy who gave it to me, and he said he's forgotten the password. So I would like to know if there's a way to get to where I can boot from the CD-ROM.

Here are some of the solutions I've read about on the net for resetting the password and why they haven't worked for me:

1-Reinstall the BIOS driver: This looks like it would work, except that these drivers all seem to be set up to only work with Windows, never with Linux.

2-Remove the CMOS battery: First of all, the CMOS battery is not accessible as far as I know, because this is a laptop. Opening it up would take resources and knowledge I don't have. Also, I've heard that on many laptops (Inspiron included) they store the BIOS password settings in FLASH memory, so that it can be stored securely without any electricity at all. (Can anyone verify this?)

 Well, I suppose that's all I can think of for now. I've tried what seems to me to be everything, and I'm getting frustrated. Can anyone give me some pointers? Thanks!
-Draken

---

### Post by ajgreeny on 2010-05-07
So how did you install ubuntu if you can't change settings in the BIOS?

Are you sure there is no F# key press to change the boot device without going into BIOS itself; many computers have this facility, though I admit I don't know whether or not that would still need the BIOS password.  Have you looked on the Dell website support or their forums for any help?

Have a look at [http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/](http://www.technibble.com/how-to-bypass-or-remove-a-bios-password/) which may be something you have not seen before, and scroll down to the manufacturers' backdoor passwords, where you may find something that can help.

Good luck.

---

### Post by Crys1sw0w on 2010-05-07
Try with a live CD. There are some programs which can kill the CMOS battery. It worked for me...

---

