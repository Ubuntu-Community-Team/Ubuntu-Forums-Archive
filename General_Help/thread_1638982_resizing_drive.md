---
title: "resizing drive"
date: 2010-12-06
forum: General Help
---

### Post by tajiknomi on 2010-12-06
[SIZE=2]I had ***unallocated space*** in on my Hard-drive and i want to get rid of it, for this i had to add/resize it to another drive, but unfortunately,i am ***unable*** to do that..... 

Screen-Shot is attached herewith

thats all...

I think for resizing , one has to ***unallocated*** more than 1 partitions to join it , isn't?
Is their another way to do it?
[/SIZE]

---

### Post by sikander3786 on 2010-12-06
Leave that unallocated. 8 MiB is not worth all those troubles :P

And I would like to see the output of this command just for the sake of posterity ;-)

```
sudo fdisk -lu
```

---

### Post by surfer on 2010-12-06
yep, i have these too. but as the unallocated space is tiny compared to the rest, i'd advise you not to bother.

---

### Post by tajiknomi on 2010-12-06
> **sikander3786 said:**
> Leave that unallocated. 8 MiB is not worth all those troubles :P

And I would like to see the output of this command just for the sake of posterity ;-)

```
sudo fdisk -lu
```

output : -

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cccef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    94092704    47046321    7  HPFS/NTFS
/dev/sda2        94092766   390716864   148312049+   5  Extended
/dev/sda5        94092768   198948959    52428096    7  HPFS/NTFS
/dev/sda6       303805278   390716864    43455793+   7  HPFS/NTFS
/dev/sda7       301443723   303805214     1180746   82  Linux swap / Solaris
/dev/sda8       198950912   301426687    51237888   83  Linux

Partition table entries are not in disk order

```

---

### Post by tajiknomi on 2010-12-06
[SIZE=2]!
[/SIZE]

---

### Post by tajiknomi on 2010-12-06
[SIZE=2]But i don't like that tiny-space as it not looking ***suitable*** in partition table;)


Any way to join it to another without formate another drive ..?
[/SIZE]

---

### Post by sikander3786 on 2010-12-06
Your partitions seem pretty Good to me. I'd advise not to bother that tiny space. Choice is yours ;-)

---

### Post by dandnsmith on 2010-12-06
I agree that the small amount of space makes the exercise a bit futile, however there is possibly a point to be made here: that screenshot shows that gparted is being run from the disk on which the OS is resident and running - you cannot do that (as the padlocks show), you have to run from a liveCD, a USBstick or another HDD for it to cooperate.

---

### Post by sikander3786 on 2010-12-06
If you are crazy about that as I see your above post, you can follow this guide.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Remember, you need all the data backed up in case some thing goes wrong ;-)

And you need to do that from a Live CD (Recommended way) or if doing from inside Ubuntu install, unmount your partitions prior to resizing.

Good Luck!

---

### Post by tajiknomi on 2010-12-06
> **sikander3786 said:**
> Your partitions seem pretty Good to me. I'd advise not to bother that tiny space. Choice is yours ;-)

[SIZE=2]Okz :p, but what are defects of joining it...?
[/SIZE]

---

### Post by tajiknomi on 2010-12-06
> **dandnsmith said:**
> I agree that the small amount of space makes the exercise a bit futile, however there is possibly a point to be made here: that screenshot shows that gparted is being run from the disk on which the OS is resident and running - you cannot do that (as the padlocks show), you have to run from a liveCD, a USBstick or another HDD for it to cooperate.

[SIZE=2]however i can move it towards sda6 , but i don't want to delete my EXTRA-drive....[/SIZE]

---

### Post by dandnsmith on 2010-12-07
I don't understand what you mean by your EXTRA drive.
Your 2 easy options are to add the space to the linux partition or to swap.

---

### Post by tajiknomi on 2010-12-07
> **dandnsmith said:**
> I don't understand what you mean by your EXTRA drive.
Your 2 easy options are to add the space to the linux partition or to swap.

[SIZE=2]Swap will not accept this unallocated space, moreover, adding this to my Gnome-Drive can cause critical harm to my OS, which i don't want,

the only option remaining is to Move this unallocated space down > so that it is ***closer to my extra drive***, then i can resize it...[/SIZE]

---

