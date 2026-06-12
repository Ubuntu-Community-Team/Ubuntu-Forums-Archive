---
title: "Hard disk partitions"
date: 2009-10-11
forum: General Help
---

### Post by mosaic2s on 2009-10-11
Using SATA HDD 80gb.
I had installed xp sp2 in the primary partition - using about 26gb.
Then installed ubuntu lts 8.04 LTS. still using it - about 24gb.
Then installed 9.04 jaunty in the 3rd partition. But now deleted it.

So i have first partition as NTFS, 2nd and 3rd as ext3.

Can I format the primary partition to ext3? Can it be done from ubuntu 8.04 LTS? Will it affect the booting?

---

### Post by LinuxRules1 on 2009-10-11
You can format the primary partition as ext3 from ubuntu using gparted.

If you want to keep your windows install then don't format the primary partition because it will erase the windows intstall.

formatting the primary partition shouldn't affect booting as long as the ubuntu installs have the boot manager and windows doesn't. 

If i remember correctly, when you install ubuntu after windows, ubuntu takes over the boot manager

to install gparted type the following command in the terminal,

```

sudo apt-get install gparted

```

---

### Post by barthel on 2009-10-11
You should be able to do it via parted, but be warned: changing your partition table can effectively wipe out your entire drive. I generally only modify partitions when I'm going to do a fresh reinstall.

If you're set up for dual booting, your XP entry will no longer work, although it shouldn't be a problem if you don't select it.

On the other hand, if your MBR is stored on the first partition, changing that partition could render your system unbootable.

</me flaps arms wildly> Danger, Will Robinson! Danger! Danger!

Back up everything that's important and make sure you have a good CD from which to reinstall. Then you can experiment without fear of catastrophic loss.

---

### Post by mosaic2s on 2009-10-11
I intend to erase xp and use the hard disk space for storage thru ubuntu LTS. No partition table is being edited.

Issue is - will I be able to boot into ubuntu after formatting the primary partition area?

---

### Post by barthel on 2009-10-11
Changing the partition type *does* change the partition table. That's one of the pieces of information stored there.

That's why we suggested using parted/gparted--you're going to have to change the partition type before you make your new filesystem with mkfs.

You should be able to boot back into Ubuntu after this. But I cannot guarantee it. That's why I recommended making the backups first--because something can always go wrong. (Murphy used to live in my cubicle.)

---

### Post by LinuxRules1 on 2009-10-11
You should still be able to boot. I believe that ubuntu takes over the boot manager/record when you install it after windows. like barthel said, i would make a backup on a cd just in case something goes wrong.

---

