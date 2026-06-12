---
title: "mapping with grub"
date: 2012-04-03
forum: General Help
---

### Post by Boxman7224 on 2012-04-03
I just joined here.  I am going to read my butt off.  I am trying to attend to a personal project that is likely an easy one for many of you but its over my head at this point.

I am using grub on a bootable flash drive to mount encrypted OS's using TrueCrypt.  I typed and use the following:

title TRUECRYPT RESCUE DISK 
find --set-root /tc.iso 
map --mem /tc.iso (hd32) 
map (hd0) (hd1) 
map (hd1) (hd0) 
map --hook 
root (hd32) 
chainloader (hd32)

This method has worked well.  I am wanting to move one of the encrypted partitions to a distant place on the drive and then map during boot so that TC thinks its still in the original location.  I know its easy to do IF I had more experience.

Can someone here give me a steer?  I am using Vista 64 and have been using TC for quite awhile.  I am actually pretty at home with imaging, encrypting, etc....

Grubb seems like an easy way to accomplish what I want to do.  Once the machine is mapped during boot everything should run the same as it does now.  Grub will only be to "trick" the machine during boot.  My GRUB bootable flash is working very well at this point.  I just want to move one of the partition OS's.

Can you help me or link me to some good reading and a how to?

---

### Post by gordintoronto on 2012-04-03
I'm sorry, but this statement: "I am using grub on a bootable flash drive to mount encrypted OS's using TrueCrypt" doesn't make any sense.

Grub is used to select which OS to boot.

---

### Post by Boxman7224 on 2012-04-04
Ok so my wording may be unclear.

I have a TC rescue disk image on bootable flash media with Grub mapping/hooking the drive as indicated by my first post on this thread.

I am trying to discover how to write the menu1st code so that I could place an encrypted OS on say the third partition and have grub map the mounting ISO, which is on the flash, to "trick" the machine into thinking its booting from the first partition.

Grub is not mounting any OS because the ISO images on the flash have the needed bootloaders.  I am only using Grub to map or drive swap (not sure which term is correct).

I have two OS's on the drive - one encrypted regular and one encrypted hidden - I would like to be able to move one and then map to a different position on the disk.

Can anyone help me with some ideas for how to do it?

---

### Post by Boxman7224 on 2012-04-04
I had this thought.  My working menulst using Grub (on bootable flash media) with two OS's on hd0 and hd1 is this:

title TRUECRYPT RESCUE DISK 
find --set-root /tc.iso 
map --mem /tc.iso (hd32) 
map (hd0) (hd1) 
map (hd1) (hd0) 
map --hook 
root (hd32) 
chainloader (hd32)


If I move the hidden OS from the second to the third partition would this work?????:

title TRUECRYPT RESCUE DISK 
find --set-root /tc.iso 
map --mem /tc.iso (hd32) 
map (hd0) (hd2) 
map (hd2) (hd0) 
map --hook 
root (hd32) 
chainloader (hd32) 


All I did is to swap the original hd1 for the hd2.  I would think this would map hd2 to hd0 and vice versa.  If it works so well using the original menulst it would seem that this would work.

Moving the encrypted partition will take many hours so I wanted to get some opinions before I waste a ton of time.

---

