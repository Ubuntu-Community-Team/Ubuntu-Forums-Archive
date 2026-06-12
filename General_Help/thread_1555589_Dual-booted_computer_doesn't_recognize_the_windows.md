---
title: "Dual-booted computer doesn't recognize the windows partition."
date: 2010-08-18
forum: General Help
---

### Post by Derek.Gildea on 2010-08-18
Hello all,

I have a gateway laptop that I have attempted to dual boot, but the computer only sees the Ubuntu OS and the Vista Windows Recovery Partition. (Actually, gnome reports 3 separate Ubuntu OSs... part of the problem?)

When I type fdisk -l, I get the following message:

[INDENT]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51e11c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581        9934    67096414+   7  HPFS/NTFS
/dev/sda4            9934       30402   164410369    5  Extended
/dev/sda5           30032       30402     2972672   82  Linux swap / Solaris
/dev/sda6            9934       29662   158464000   83  Linux
/dev/sda7           29662       30031     2970624   82  Linux swap / Solaris

Partition table entries are not in disk order
root@grendel:~# [/INDENT]

Now, I know that my windows partition rests on sda3. And I note that sda3 ends on the same block as sda4 begins, 9934. 

Could this be the problem? and if so, how do I deal with it?

Best Wishes,

Derek

---

### Post by oldfred on 2010-08-18
With windows7 you have a 100MB boot/recovery partition which is the active (boot flag) partition or sda2.

If you want to see if data overlaps you have to use this as fdisk by sectors may have partitions start in the middle now. I doubt if you have a problem.

```
sudo fdisk -lu
```

It is a little strange to have two swap partitions. Did you install twice?

To see more details on your install.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Derek.Gildea on 2010-08-19
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51e11c3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    25173854    12586896   27  Unknown
/dev/sda2   *    25173855    25382699      104422+   7  HPFS/NTFS
/dev/sda3        25382700   159575528    67096414+   7  HPFS/NTFS
/dev/sda4       159576062   488396799   164410369    5  Extended
/dev/sda5       482451456   488396799     2972672   82  Linux swap / Solaris
/dev/sda6       159576064   476504063   158464000   83  Linux
/dev/sda7       476506112   482447359     2970624   82  Linux swap / Solaris

This doesn't look right. sda4 and sda5 end on the same block - I've got linux swap on two separate partions... is it possible to rewrite this partition table? or would I be better off deleting all partitions and starting from scratch?

---

### Post by varunendra on 2010-08-19
> **Derek.Gildea said:**
> 
/dev/sda4       159576062   488396799   164410369    5  Extended
/dev/sda5       482451456   488396799     2972672   82  Linux swap / Solaris
/dev/sda6       159576064   476504063   158464000   83  Linux
/dev/sda7       476506112   482447359     2970624   82  Linux swap / Solaris

This doesn't look right. sda4 and sda5 end on the same block

[COLOR=Red]**This is perfectly right !**[/COLOR] sda5, 6, 7 are your logical drives, while sda4 is the **'Extended Partition'** containing them.

You may already know that an extended partition is just a container for 'logical drives', so it obviously **starts from (or just before) the block where its first logical drive starts **(provided there is no unpartitioned space at the beginning of extended partition) **and ends at (or just after) where its last logical drive ends** (again- provided there is no blank space left there).

See the graphical representation of your drive by GParted and the read above for a better understanding.

In your case, **sda4 is extended partition**, sda6 is first logical drive in it, sda7 second and sda5 is the last logical drive. So it (sda4) ends where sda5 (last) is ending.

You might wonder why 'first' is numbered as 6 while 'last' as 5. This may happen due to the sequence in which the drives are created (or recreated).

FYI, logical drives always start with no.5. Nos. 1 to 4 (e.g., hda1/sda1.......sda4) are reserved for 'Primary Partitions' (Extended partition is seen by the BIOS as a primary partition; it is the OS/boot-loader that recognizes the logical drives in it.). Conventionally, max. no. of Primary Partitions can be 4 (that's why 5 onwards is assigned to logical ones).


**Okay, enough torturing you (I guess most of this you already knew ;)), now back to your problem-**

Please post the output of Boot Info Script as Fred asked you....


**_PS_: **Please post the screenshot of GParted also as a backup description of partition layout (actually to let me know how many errors I've made in the above lecture..err...). Kidding, just realized that sda5 & sda7 seem to be adjacent swap partitions (unnecessarily), the screenshot would confirm this.

---

### Post by Quackers on 2010-08-19
Have you tried booting the Windows Recovery partition? I ask because my vista partition is actually labelled as "vista recovery" by grub, and it boots into Windows just fine.

---

### Post by Mark Phelps on 2010-08-19
There have been reported problems with GRUB2 and Win7 where GRUB 2 mislabels the partitions, such that, in order to boot into the correct Win7 partition, you have to choose the one labeled Recovery.

Try that and see if that works.

---

