---
title: "Help!!! ipod not working"
date: 2006-03-20
forum: General Help
---

### Post by badkarmax on 2006-03-20
Hi,
I am new to ubuntu(breezy badger 5.10, gnome) and linux. I was trying to connect my ipod. Read many threads and jumped in, to connect my ipod.
My ipod is ipod image 30GB.

Problems:
If i connect my ipod. I can see the icon on desktop and thru nautilus. I cud even see the entry for ipod in /etc/mtab. If i umount the  ipod thru console or from desktop, the icon goes off but my ipod still shows message as connected do not remove. After this if i plug out and then plug in ipod.The icon does not show up.

I tried amarok (version 1.3.7). It crashes straight wen i connect ipod. Tried banshee (version 0.9.7) does not do anything. Tried gtkpod, it shows me all songs from ipod. When i try to play any song, it doesn't play. Snycing also gives error.

I tried: sudo dosfsck -a /dev/sda2
i get following output:
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Read 512 bytes at 0:Input/output error

I even tried dmesg. While connect time no errors were shown but later doing dmesh showed up many errors. Some error messages at various intervals of time of some relevance by using dmesg are:

[4300882.867000] scsi0 (0:0): rejecting I/O to offline device
[4300882.867000] FAT: Directory bread(block 76080) failed
[4300883.563000] scsi0 (0:0): rejecting I/O to offline device
[4300883.563000] FAT: unable to read inode block for updating (i_pos 1220301)
[4300883.868000] scsi0 (0:0): rejecting I/O to offline device
[4300883.868000] FAT: Directory bread(block 76080) failed
[4300884.869000] scsi0 (0:0): rejecting I/O to offline device
[4300884.869000] FAT: Directory bread(block 76080) failed
[4300885.870000] scsi0 (0:0): rejecting I/O to offline device
[4300885.870000] FAT: Directory bread(block 76080) failed
[4300886.871000] scsi0 (0:0): rejecting I/O to offline device
[4300886.871000] FAT: Directory bread(block 76080) failed

and

[4303838.605000] Buffer I/O error on device sda2, logical block 76144
[4303838.605000] lost page write due to I/O error on sda2
[4303860.986000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303860.986000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303861.078000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303861.078000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303888.937000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).

Help me out please!!!!!

---

### Post by IYY on 2006-03-20
Have you tried playing the songs using rhythm-box?

---

### Post by badkarmax on 2006-03-20
yup tried rythmbox. Rythmbox also crashes abruptly.

---

