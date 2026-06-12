---
title: "Reconfiguring System"
date: 2010-10-24
forum: General Help
---

### Post by katykat on 2010-10-24
My system is currently: 

Primary : 
master sda1 -XP
slave - Jaunty

Secondary:
master : Cdrom 
slave : Meerkat

By default the system boots to Meerkat. 
All works fine. 

I intend to replace the XP drive with a much larger one and KEEP it the primary as SDA1. 
This is not optional. 

Also I *must* put the CDROM as the SLAVE of the PRIMARY channel. I know how to change jumpers. 

On the secondary channel I want to to put the Jaunty drive where the CD *was*  and upgrade the Jaunty to Lucid and Keep Meerkat where it is as slave, and as the main boot drive. 

This is my question:

I intend to change the drives around BEFORE I change the XP SDA1 over. 

Will there be any boot problems with the drives reconfigured, and if so, can grub2 be reconfigured before startup, or be told to reconfigure on startup?

AFTER the XP is upgraded to a larger drive on SDA1, will there be problems on booting? 
It will at that time have the XP MBR. How would I get to grub to tell it to update the XP drive MBR?

---

### Post by katykat on 2010-10-25
Perhaps if i put it more simply;

Would changing the drives around between the HD controllers (while keeping a Win SDA1 as primary boot, affect the booting of Grub2?

And...

How do i get a new Windoze drive to see grub2 instead of its NTLDR?

Many thanks in advance. 
Over the years I have been running Linux on and off since version 0.9.
I feel this latest version is a keeper....
(Jaunty was driving me nuts, especially with an nvidia card.)

---

### Post by katykat on 2010-10-25
There was an alternative to boot loaders, as I've never cared for them. 

Is there a modern equivalent to LOADLIN?

I used to boot my Linux kernels at bootup in DOS, and it would switch over to the ext2 drives/partitions. 

Anything similar these days?

---

