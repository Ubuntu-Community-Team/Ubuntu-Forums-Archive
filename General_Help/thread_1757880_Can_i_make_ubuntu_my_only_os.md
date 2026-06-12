---
title: "Can i make ubuntu my only os?"
date: 2011-05-13
forum: General Help
---

### Post by ChinaManLiu808 on 2011-05-13
Hey so i was wondering if i could just delete vista and make ubuntu my os? Thanks

---

### Post by white_rabbit0 on 2011-05-13
yes. To make ubuntu your only os first backup all your files as you will lose them during the install. Next take the live cd and insert it into the disk drive. Restart your computer and when you do make sure that the the bios settings are set to boot from the cd drive before hard drive. This will make your computer run from the live cd and when you are ready to do so select to install ubuntu. When you do this a box will pop up and will give you some options you want to make it your only os so you want to erase the disk. Now this will make you lose all your files that you had on the computer before. But if you are sure then select it. This will erase everything and make ubuntu your only os.

---

### Post by wilee-nilee on 2011-05-13
> **ChinaManLiu808 said:**
> Hey so i was wondering if i could just delete vista and make ubuntu my os? Thanks

Yes if you don't have Ubuntu installed inside of it=wubi, if you do removing Vista will remove Ubuntu.

If you have wubi install it can be transferred to a partition, so you can remove Vista and keep the Ubuntu install.

---

### Post by ChinaManLiu808 on 2011-05-16
so what if i already have ubuntu installed on a separate partition. can i just delete the partition with vista on it and then add the two together? thanks

---

### Post by Hedgehog1 on 2011-05-16
To answer what partitions can be deleted and which can be 'resized' to use the open space created by deleted the windows partitions, we need to see your partition layout.

This is the fastest way to show this information to us:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by seawolf167 on 2011-05-16
If you installed Ubuntu via WUBI, you can migrate it to it's own partition by following the instructions in [this post ]("http://ubuntuforums.org/showthread.php?t=1519354")(scroll down for the automated script).

If you installed via the LiveCD on it's own partition, it is as simple as deleting the partition with Vista with GParted, the resizing your partition (/ or /home) into the now unallocated space while booted off a LiveCD.

---

