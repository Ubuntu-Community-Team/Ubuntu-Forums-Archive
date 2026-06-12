---
title: "howto: erase the grafical interface"
date: 2005-02-15
forum: General Help
---

### Post by voda on 2005-02-15
Hi,

I want to erase the grafical part of ubuntu, when i allready installed ubuntu. Is that possible? If yes, how?

---

### Post by az on 2005-02-15
sudo apt-get remove gdm.

You may also remove xlibs and the gnome libraries (libgnome).  That should wipe most of the graphical stuff away.  Next time, just install with the "custom" option.

---

### Post by voda on 2005-02-15
Thanks.

ANother quistion.

I have an error 18 when i boot my computer. I know why because i'm running an old bios (phoenix bios 4.05) and my harddisk is 20 gb. Where can i change it in the bios and what? I read something about Changing the Hdd mode, but I can't find it. I also read something about the LBA setting in the BIOS. Cant find it either. I looked for the manual of the 4.0 bios, but it's totally different with the BIOS of mine. Someone know what to do? And yes i allready read this: [http://www.ubuntuforums.org/showthread.php?t=11764](http://www.ubuntuforums.org/showthread.php?t=11764)

---

### Post by El Guapo on 2005-02-15
I updated my BIOS just to be able to run live cd's and such  a while ago.  This might do it for you.

---

### Post by voda on 2005-02-15
how do i update it? floppy cd?

---

### Post by Wim Sturkenboom on 2005-02-16
You need the new BIOS and a tool to write it. Both can be found on the site of your motherboard manufacturer. Instructions can be found there as well.
Most common is to use a bootable (DOS) floppy, but I don't see why a bootable CD would not do the trick. Add the downloaded files to it and boot from it.

Floppy has the advantage that you can backup the old BIOS before starting the upgrade (CD does not offer this).

---

