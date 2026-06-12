---
title: "What is going on with my Ubuntu..."
date: 2011-11-07
forum: General Help
---

### Post by Butterfly-Love on 2011-11-07
I downloaded the latest 64bit 11.10 Ubuntu..

I installed using wubi

After rebooting.. 

Nothing happens, there is no selection to start with ubuntu...

---

### Post by bluexrider on 2011-11-07
This assumes you installed using windows. If thats the case then fix your MBR. 

Windows XP
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

Windows 7
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html) 

Otherwise boot from the Live CD/DVD and Follow this thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Rubi1200 on 2011-11-07
The OP clearly stated the following:

> I installed using wubi


Therefore, any instructions to restore the Windows bootloader or GRUB will be ineffectual _unless_ Windows is not booting (which does not appear to be the case from the description given).

@Butterfly-Love;
please post the specifications for the computer and also post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Butterfly-Love on 2011-11-07
Hi, as of now i don't even have linux installed. How am i supposed to run the bash script??

I use a G72 HP laptop

i3 (M350 @ 2.27GHz), 4G ram, 500GB harddrive, Intel(R) HD Graphics....

---

### Post by Butterfly-Love on 2011-11-07
> T
please post the specifications for the computer and also post the results of the boot info script.
There is a link at the bottom of my post with instructions.


help``````

---

### Post by Mark Phelps on 2011-11-07
Read the instructions ... it also says you can boot with a LiveCD.

So, you will need an Ubuntu desktop CD whose version matches what you tried to install with Wubi (i.e., 11.10, 11.04, etc)

---

