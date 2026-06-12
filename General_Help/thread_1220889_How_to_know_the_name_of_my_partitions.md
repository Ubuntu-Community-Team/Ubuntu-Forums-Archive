---
title: "How to know the name of my partitions?"
date: 2009-07-23
forum: General Help
---

### Post by miros84 on 2009-07-23
Hi. I have 2 HDD with 1 partition and 1 HDD with severals particion. When I type fdisk -l I have:

/dev/[COLOR="Red"]sdb1[/COLOR]   *           1         127     1020096    b  W95 FAT32
/dev/[COLOR="Red"]sdb2[/COLOR]             128       24321   194338305    5  Extendida
/dev/[COLOR="Red"]sdb5[/COLOR]             128        3049    23470933+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb6[/COLOR]            3050       16671   109418683+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb7[/COLOR]           16672       19221    20482843+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb8[/COLOR]           19222       21771    20482843+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb9 [/COLOR]          21772       24321    20482843+  83  Linux

these 7 partition for the thirth HDD and I see the [COLOR="Red"]names[/COLOR] for every partition: [COLOR="Red"]sdb1, sdb2, sdb5, sdb6, sdb7, sdb8, sdb9.[/COLOR]
But I dont know which particion correspond to which name is...
I mean, my 7 partition are, Windows, Vista, My files, Ubuntu,.........
But I dont know if Windows is sdb1 or sdab2 or sdab6. How can I see that?

---

### Post by MrWES on 2009-07-23
> **miros84 said:**
> Hi. I have 2 HDD with 1 partition and 1 HDD with severals particion. When I type fdisk -l I have:

/dev/[COLOR="Red"]sdb1[/COLOR]   *           1         127     1020096    b  W95 FAT32
/dev/[COLOR="Red"]sdb2[/COLOR]             128       24321   194338305    5  Extendida
/dev/[COLOR="Red"]sdb5[/COLOR]             128        3049    23470933+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb6[/COLOR]            3050       16671   109418683+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb7[/COLOR]           16672       19221    20482843+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb8[/COLOR]           19222       21771    20482843+   7  HPFS/NTFS
/dev/[COLOR="Red"]sdb9 [/COLOR]          21772       24321    20482843+  83  Linux

these 7 partition for the thirth HDD and I see the [COLOR="Red"]names[/COLOR] for every partition: [COLOR="Red"]sdb1, sdb2, sdb5, sdb6, sdb7, sdb8, sdb9.[/COLOR]
But I dont know which particion correspond to which name is...
I mean, my 7 partition are, Windows, Vista, My files, Ubuntu,.........
But I dont know if Windows is sdb1 or sdab2 or sdab6. How can I see that?

Try
```
df
```in a terminal; it'll show you the mount point and that might help.

~Bill

---

### Post by drs305 on 2009-07-23
```
sudo blkid
```
It will show the UUIDs and any assigned labels. Note these are the labels and not the mount points. The current mounted partitions can be seen by running the command "mount"

---

### Post by miros84 on 2009-07-23
> **drs305 said:**
> ```
sudo blkid
```
It will show the UUIDs and any assigned labels. Note these are the labels and not the mount points. The current mounted partitions can be seen by running the command "mount"

Thank you very much. That helped me a lot. Last questions.
sdb5 means hd(1,4)?

---

### Post by drs305 on 2009-07-23
> **miros84 said:**
> Thank you very much. That helped me a lot. Last questions.
sdb5 means hd(1,4)?

For grub (legacy) yes. For grub 2, it would be hd(1,5).

---

### Post by miros84 on 2009-07-23
> **drs305 said:**
> For grub (legacy) yes. For grub 2, it would be hd(1,5).

Thank you for your help. I see you understand this, I would like ask you another questions. :)

I have installed windows in [COLOR="Red"]sdb5[/COLOR], so I put [COLOR="Red"]hd(1,4[/COLOR]) in my menu.lst file and that worked for me. I can run windows well, but I dont understand how it works, because I have the [COLOR="Black"]**boot.ini, ntldr and ntdetect.com**[/COLOR] in another partition - [COLOR="DarkGreen"]sdc1[/COLOR], which means [COLOR="DarkGreen"]hd(2,0)[/COLOR]
I dont have [COLOR="Black"]**boot.ini, ntldr and ntdetect.com**[/COLOR] in [COLOR="Red"]hd(1,4)[/COLOR] where is my windows.
Is that mean that grub dont need [COLOR="Black"]**boot.ini, ntldr and ntdetect.com**[/COLOR] to boot windows? I dont think so, because my menu.lst is:

title Windows XP (Loader)
root [COLOR="Red"](hd1,4)[/COLOR]
chainloader +1

and when I start my PC, if I choose "Windows XP (Loader)"
then I see the menu from the boot.ini of my [COLOR="DarkGreen"]sdc1[/COLOR] disk.
I repeat, I have do not [COLOR="Black"]**boot.ini, ntldr and ntdetect.com**[/COLOR] in my ([COLOR="Red"]hd1,4[/COLOR]) that I use in my menu.lst.
Can you explane me how this work?

---

### Post by drs305 on 2009-07-23
> **miros84 said:**
> 
Can you explane me how this work?

It's been a while since I've worked with the Windows boot loader, but I can give you the basics.

The grub menu entry for Windows include "chainloader +1". What that does, in simple terms, is to tell grub to turn over the boot process over to another boot loader. So grub sends the boot process control over to Windows, and Windows knows where to look for it's own boot files. Since Windows now controls the process, grub really doesn't need to know where those additional files are. Windows does, and thus points to the correct locations for the Windows files you mentioned.

---

### Post by miros84 on 2009-07-23
So, if I want to add windows xp, vista or windows 7, I just have to add these lines

title Windows XP (Loader)
root (hd1,4)
chainloader +1

and put the correct root, right? I mean, this is the same for another windows like vista and 7?

---

