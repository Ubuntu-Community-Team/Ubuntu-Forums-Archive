---
title: "Unknow boot problem."
date: 2010-09-04
forum: General Help
---

### Post by jkb609gi8 on 2010-09-04
My old laptop has a broken screen. I tried using an external flat screen and win-xp would not run this screen. This is how I came to learn about Ubuntu. I loaded Ubuntu 9.4 and the computer worked with the external screen.

The only problem was that during the boot process the (kernal text?) the white text on black screen over ran the edges of the external screen. Once the Ubuntu was loaded the window fit the screen perfect.

Now my new problem. After a year of perfect use, the battery ran down and the computer shut itself off. When I put the charger back on and rebooted the laptop, the ubuntu partly opens then hangs up on the kernal (white text on black screen) because of the screen overrun problem I can not read the text.

I can boot still boot from the 9.4 CD. 

Is there anyway I can correct the problem by re-installing 9.4 but not wiping out my person data and files. In other words is there any way to repair the O/s that is defective, without losing my work?

---

### Post by DeMus on 2010-09-04
> **jkb609gi8 said:**
> Is there anyway I can correct the problem by re-installing 9.4 but not wiping out my person data and files. In other words is there any way to repair the O/s that is defective, without losing my work?

It depends how you installed it.
Did you do a "normal" install (without Wubi I mean)?
Did you make a separate home folder? (partition)
If both questions can be answered with yes then you can re-install the OS without loosing your data. You do have to remember which partition is your home partition, you can see that looking at the size of it. During installation (step 4) you have to choose manual partitioning. You will see the present partitions and choose the one you used for "/". Choose to use it for "/" again, format it as Ext3 or Ext4 (whatever you like).
Then choose the one you used for "/home", choose Ext3 or Ext4 (same as you used in the original installation), select to use it for "/home" again **[COLOR="Red"]BUT DON'T FORMAT IT[/COLOR]**.
Then continue the installation and you'll be fine.
One thing, use the same login name as you used before to become owner again of your home directory.
Success.

---

### Post by jkb609gi8 on 2010-09-05
The way I installed Ubuntu 9.4 was from a Cannonial supplied disc, I chose to formatte the harddrive removing the winsxp O/S. There is no partition that I now about.
I do not know what Wubi is or means.
Well maybe there is a partition now that I think about it, however it was install as per Cannoncial's disc.

Did you make a separate home folder? (partition) I do not think so.

"" You do have to remember which partition is your home partition, you can see that looking at the size of it. "" I do not know if ubuntu has a hidden partition? (Like windows?)

How does a person enter a partition manager (eg. windows) to see how this laptop is partitioned?

Any ways if I do not see anymore suggestions, I will try to follow the above instructions.

   *****************

I have typed what text I can see from the broken laptop, in the hope someone might reconize the problem. (As follows below)


trying to resume from /devdisk/by-uuid/97610070-46d5-46de-b306-18c

No resume image. doing normal boot...
mounting /dev/disk/by-uuid/75011af8-8243-48d1-8195-d00eb3ecaca6 on
: Invalid argument
mounting /dev on /root/dev failed: No such file or directory
mounting /sys on /root/sys failed: No such file or directory
mounting /proc on /root/proc failed: No such file or directory
filesystem doesn't have /sbin/init.
t found. Try passing init= bootarg.

x v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
'help' for a list of built-in commands.

amfs) _


This above is all I can read. A small amount of the the text from left side of the screen is missing. The last letters (that being amfs) is followed by a flashing cursor.

---

