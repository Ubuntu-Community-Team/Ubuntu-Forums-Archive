---
title: "Change Ubuntu Partition with files Intact"
date: 2011-04-20
forum: General Help
---

### Post by rez182 on 2011-04-20
Im in a live CD session right now and copying the **main** ubuntu partition to a **new **partition. basically im doing this to install windows and have a separate partition for STUFFs like videos etc. since i cant have more than 4 primary partitions. win7 takes up 2 partitions and ubuntu takes 1 and an extended which will have swap and "STUFFs". i know how to reinstall the grub but i dont know the other stuffs. if someone can please help me out step by step will be great. thanks alot..

---

### Post by Hedgehog1 on 2011-04-20
> **rez182 said:**
> Im in a live CD session right now and copying the **main** ubuntu partition to a **new **partition. basically im doing this to install windows and have a separate partition for STUFFs like videos etc. since i cant have more than 4 primary partitions. win7 takes up 2 partitions and ubuntu takes 1 and an extended which will have swap and "STUFFs". i know how to reinstall the grub but i dont know the other stuffs. if someone can please help me out step by step will be great. thanks alot..

I am doing a little guessing here:  You are copying your primary partition of Ubuntu to a logical partition using gparted, yes?

This:

[B]/dev/sda1 System
/dev/sda2 Windows
/dev/sda3 Ubuntu[/B]

Will become this:

[B]/dev/sda1 System
/dev/sda2 Windows
/dev/sda3 Ubuntu
/dev/sda4 Extended
__/dev/sda5 copy of /dev/sda3 Ubuntu[/B]

And then you will add a swap partition:

[B]/dev/sda1 System
/dev/sda2 Windows
/dev/sda3 Ubuntu
/dev/sda4 Extended
__/dev/sda5 copy of /dev/sda3 Ubuntu
__/dev/sda6 Swap[/B]

If this is what you are doing, once you have copied the the Ubuntu partition and added the swap, you will need to update the /etc/fstab file in /dev/sda6 to use the new UUIDs from /dev/sda5 and /dev/sda6.

You will also need to reinstall grub from the LiveCD/LiveUSB.

Then you can remove the /dev/sda3 partiton and reused it for 'stuff'.

**Is this what you are looking to do?**


***The Hedge***

:KS

---

### Post by rez182 on 2011-04-20
the for mat is a bit diff.. i didnt install win7 yet. ill move ubuntu to a new place n place win in the old one.
right now its like this. tell me if there is anything wrong...

[B]dev/sda1 - main ubuntu
dev/sda2 - new ubuntu (copied)
dev/sda3 - extended
dev/sda5 - swap
dev/sda6 - ntfs (stuffs)

[/B]since win7 takes up space for system, after in install it, the format will change to (i guess):

[B]dev/sda1 - system
dev/sda2 - win7
dev/sda3 - ubuntu
dev/sda4 - extended
dev/sda5 - swap
dev/sda6 - ntfs (stuffs)

is it correct?

[/B]will i get the new UUID in **sudo blkid **? n update both the UUIDs in fstab n the **initrams?**

---

### Post by rez182 on 2011-04-20
apparently win7 cant make they system partition with this format. getting really frustrated, thinking of deleting everything and doing a fresh start. its been only 1 month i use ubuntu and already i did about 3 reinstalls of ubuntu. this time i have to set it right...i dont have patience anymore....so thanks Hedgehog1 for ur help...ill jus delete everything...

---

