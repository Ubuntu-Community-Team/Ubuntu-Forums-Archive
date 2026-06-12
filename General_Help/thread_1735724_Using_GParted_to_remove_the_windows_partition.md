---
title: "Using GParted to remove the windows partition"
date: 2011-04-21
forum: General Help
---

### Post by amathew on 2011-04-21
First post. Ubuntu newbie here.

I was trying to remove my windows partition using the live CD. While Windows no longer works on my system, GParted shows that I still have 40 gb of unallocated space. Have I not properly occupied the space left after I removed the Windows partition.

---

### Post by lithopsian on 2011-04-21
A picture would be helpful.  Or at least a list of your partitions.  If you just deleted the partition, you will be left with unallocated space.  Then you would extend another partition to include that space.

---

### Post by amathew on 2011-04-21
unallocated--unallocated--39.54 GB
/dev/sda4--extended--31.49 GB
/dev/sda5--ext4--31.49 GB
unallocated--unallocated--3 MB
/dev/sda6--linux-swap--1.34 GB
unallocated--unallocated--3.44 GB

---

### Post by lithopsian on 2011-04-21
OK, so you have 40GB unallocated at the start of the drive, Ubuntu on an extended partition, and then swap plus another few GB unallocated at the end of the drive.   You can't extend the Ubuntu partition to include the unallocated 40GB because it is not on the same extended partition.  You will have to extend the extended partition to include the unallocated space before you can extend the Ubuntu partition to include that space.  The space at the end of the drive cannot be combined with the Ubuntu partition.

---

### Post by wilee-nilee on 2011-04-21
Post a picture of gparted you may need to install it in Ubuntu.
sudo apt-get install gparted

Just your hand typed description to go on is a precarious method.

Also moving the front of any bootable partition will require a reload of grub to the mbr.

---

### Post by amathew on 2011-04-21
I'm running GParted through the live CD.

[IMG]http://img202.imageshack.us/img202/542/screenshotln.png[/IMG]

---

### Post by wilee-nilee on 2011-04-21
So you notice the keys on sda5 and sda6 partitions, right click sda6 and then swap off. Now everything is ready to be moved move the extended=sda6 to the left first then the sda5 partition to the left.

I'm assuming that is what you want, the key here is turning off the swap.

If you want to extend the sda5's right end towards the end, you can remove the swap expand the ext-sda6 to the right, make a new swap and expand the sda5 up to the swap. Swap can actually be anywhere in that extended so I think you get the idea.

You will need to reload grub after this more then likely, no big deal though, just follow the first couple of commands from this link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

The other poster was correct personally I want to be sure thats all.

---

### Post by amathew on 2011-04-21
It keeps giving me a "Could not deactivate swap" error message


Would it be easier just to use the cd to reinstall ubuntu. That way I can just customize the partition during the installation process.

---

### Post by wilee-nilee on 2011-04-21
> **amathew said:**
> It keeps giving me a "Could not deactivate swap" error message


Would it be easier just to use the cd to reinstall ubuntu. That way I can just customize the partition during the installation process.

It looks like you have very little on the partition anyway, yeah go for a install, the moving of the partition....etc would take a bit longer most likely.

Kinda of strange that you can't turn of the swap though, shouldn't matter though if you just overwrite the whole disc.

---

