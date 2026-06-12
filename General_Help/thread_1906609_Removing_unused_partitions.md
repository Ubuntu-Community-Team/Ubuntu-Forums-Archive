---
title: "Removing unused partitions"
date: 2012-01-09
forum: General Help
---

### Post by wvcaudill2 on 2012-01-09
Hello all, I would like to remove an old swap partition that is no longer used. In the attached screenshot, you can see my GParted, and the partition, /dev/sda5/, that I would like to remove.

The problem is, when I try to remove it, I get a message saying:

Please unmount any logical partitions having a number higher than 5

My question is, how do I do this? And is it safe to do this?

---

### Post by Basher101 on 2012-01-09
to delete it you must first unmount your used swap. to do this rightclick on the swap partition with /dev/sda7 (you can see a small key next to it) and choose unmount from the dropdown menu. you can then proceed to deleting it.

edit: you may need to boot from a Live CD to unmount it

regards

---

### Post by Paqman on 2012-01-09
You'll actually need to boot up into your LiveCD or USB for this. Boot up, open Gparted, right click on your swap partition and "swapoff", then you'll be able to make any changes you want.

---

### Post by imachavel on 2012-01-09
I myself have had problems with this where I try and unmount or unswap and it won't let me. Partitions must be contiguous. I believe sometimes if they aren't, the disk won't allow you to unmount it. This is strange considering if you boot to gparted, you haven't mounted the files system, you aren't using the OS, so why in the world does it not allow you to unmount and delete it? 

I'm not sure though using gparted when the OS isn't mounted is the safest way so if you can't do it through there, I don't know if there is a better idea

---

### Post by wvcaudill2 on 2012-01-09
Ok guys, so bottom line is that unmounting and renaming partitions that my system currently uses is safe and wont create any problems?

I think what I have to do is load the LiveCD, and unmount sda5/6/7, then delete the sda5, and then rename 6 to 5, and 7 to 6?

Please confirm that this is the correct procedure.

---

### Post by Basher101 on 2012-01-09
> **wvcaudill2 said:**
> Ok guys, so bottom line is that unmounting and renaming partitions that my system currently uses is safe and wont create any problems?

I think what I have to do is load the LiveCD, and unmount sda5/6/7, then delete the sda5, and then rename 6 to 5, and 7 to 6?

Please confirm that this is the correct procedure.

its the correct procedure.
I do not remember correctly, but the naming goes on the order and number of partitions on your disc, i think mine were renamed without me doing anything, so that may be automatic...

regards

---

### Post by wvcaudill2 on 2012-01-09
Ok guys, I seem to have run into a problem. I decided to delete the sda5 partition, and with the free space, create a ntfs partition. However, when I rebooted the system I get a GRUB error: unknown file system. 
grub rescue>

Can anyone tell me how to fix this?

---

### Post by imachavel on 2012-01-09
well I don't understand how deleting a partition, recreating it, then renaming it will fix anything. I mean, now the partition is gone. A partition is unused when no OS is installed on it, and no swap space is installed. Then you can delete it and recreate it and I guess rename it. But you probably deleted a partition that grub was installed on. Be very careful when doing this. Deleting hard disk space is never ever EVER EVER EVER EVER entirely safe. There are RISKS of data loss. and I'm guessing when you decided to delete the space it said so before you deleted it.

I'd say boot to the live cd then read out the command grub.conf, but honestly, I don't know too much about this.

---

### Post by Basher101 on 2012-01-09
[http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html](http://www.upubuntu.com/2011/08/how-to-repairreinstall-grub-boot-loader.html) to fix it


regards

---

### Post by wvcaudill2 on 2012-01-09
Quick question, how do I know where my GRUB was previously installed? I think I need to either overwrite it, or delete it, because it doesnt make much sense for me to have two different GRUBs

---

### Post by Basher101 on 2012-01-09
> **wvcaudill2 said:**
> Quick question, how do I know where my GRUB was previously installed? I think I need to either overwrite it, or delete it, because it doesnt make much sense for me to have two different GRUBs

there was some program you could run that shows you all partitions and bootloaders...not sure what it was called, you might find it on the forums when searching for boot problem related threads...

---

### Post by wvcaudill2 on 2012-01-09
I got everything taken care of now, thanks for your help everyone!

---

### Post by Basher101 on 2012-01-09
> **wvcaudill2 said:**
> I got everything taken care of now, thanks for your help everyone!

great^^ mark your thread as [SOLVED] with the thread tools at the top right :popcorn:

---

