---
title: "Help reinstalling windows?"
date: 2011-08-21
forum: General Help
---

### Post by JordanMS on 2011-08-21
Hello, I've recently needed to reinstall my windows OS. (Sony Vegas, Games, Ect) Aparently my computer had a backup partition for restoring (I accidently removed my Windows 7 OS) and I need to reinstall. I can't seem to find my partition, So I burned a copy of  Windows Vista. Everything goes smoothly until I come up saying it cannot install because the partition needs to be a NFTS (sp?) partrion. I've tried Gparted but not all of the options will come up for me in it. I'm using Natty at the moment aswell. Help? :C

---

### Post by oldfred on 2011-08-21
Grub should also give you the option to boot to the recovery partition. But that usually just is an image of the entire hard drive and totally restores it to as purchased. You then have to rerun all updates & reinstall Ubuntu.

Windows  will only install to a primary partition, formated NTFS with the boot flag (active partition in windows) or to unallocated space with a primary partition (sda1 thru sda4) available.

You can only really use gparted from a liveCD as it cannot work on mounted partitions, and even with liveCD you have to right click on the swap and swap off to unmount it as liveCDs usually use swap to speed things up.

---

### Post by Mark Phelps on 2011-08-21
If your PC came with Vista preinstalled, it might have also come with a Restore CD.  If that is true, all you then have to do is boot from that CD.  It will start the Restore program.

If there was no CD, then you generally have to press a Function key to start the Restore operation.  The key varies by PC model (will tell you which it is in the documentation that came with the PC), but keys used typically include F8 and F11.  You can try pressing one after another until you exhaust them all.

Also, if you reintall using a Vista DVD, not only will have have to then reinstall everything, but you will most probably have to reactivate it as well.  So, look around for the sticker containing the activation key.  You might need that.

---

### Post by Agzander101 on 2011-08-21
go to your manufacturers website to see what the key is to boot up the restore partition.

 if you get windows running i highly recommend that you make a factory restore disk.  this will help you bring your computer back to state as if it was right when it came out of the box. its very useful especially  if something ruins/deletes your recovery partition.  good luck :).

---

### Post by RJ12 on 2011-08-21
Hopefully the recover partition still works... On my old laptop (Toshiba) once you changed the partitions, the recover partition no longer worked. I found out the hard way!

---

