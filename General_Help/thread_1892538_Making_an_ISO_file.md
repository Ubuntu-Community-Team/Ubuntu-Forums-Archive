---
title: "Making an ISO file"
date: 2011-12-08
forum: General Help
---

### Post by gonnamakeadistro on 2011-12-08
Hello,
This is my first post on Ubuntu Forums,
Well Ive been 2 months looking for a way to make a mini distro that, when you boot up the system (don't care if is a live cd) there is a command prompt. Yesterday I looked on the Ubuntu Minimal CD (mini.iso)
I extracted the iso and modify it, but know How do I make the ISO again? I tried to do this in the terminal:
mkisofs -o /usr/src/my-mini-distro.iso /home/dimitri/Downloads/my-mini-distro
That last thing was the directory whrere I extracted the files and modify them.
I burned it in a CD and when my computer boots up, It says:
Boot from cd:
And it waits, and it boots Ubuntu,
Does anyone how to make the iso bootable?
It has the same as the Ubuntu Minimal cd, I only modified the splash, I remove it and delete the line in the boot loader where it says: saplash.png (to load it)
Does anyone know how to make a mini distro that boots up and gives you a command prompt (could be bash)??
Thank You,
Sorry for my English, as you can see Im not English...
See ya!

---

### Post by dandnsmith on 2011-12-08
I know what is lacking, and is used with Ubuntu to get it booting - it's called Syslinux.
However I've never tried to see how to integrate it into a CD, as you're trying to do

---

### Post by gonnamakeadistro on 2011-12-08
Thanks, useful information.
Do you know any manual or tutorial to make a distro tht boots and it gives you a command prompt??
Thanks!!
------------------------------------------------
:D

---

### Post by dandnsmith on 2011-12-09
I suggest googling with either 'make bootable cd from iso' or 'make bootable usb from iso' - both give lots of results, some of which look to get you what you want (like magiciso and ezboot)

HTH

---

