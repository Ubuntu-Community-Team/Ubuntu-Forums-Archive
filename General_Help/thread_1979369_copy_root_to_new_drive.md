---
title: "copy root to new drive"
date: 2012-05-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-05-13
i have a need to copy my root partition to a new drive i could use gparted but that would copy empty space so is there a way to use [FONT=Courier New]rsync[/FONT] to copy everything and not follow sym links but copy the link it self or should i use a [FONT=Courier New]cp -r[/FONT]?
basically i want to copy sda3 to sdb1 (it is empty) and i want it to be boot able (giving i will have to fix the MBR)
[FONT=Courier New]cp -r /media/old/* /media/new/[/FONT]
would that work from a live cd?

---

### Post by WorMzy on 2012-05-13
If you're going to use cp, use the -p flag to preserve permissions. I believe that -d would do what you want regarding links, but check the man page yourself to make sure.

Also, remember to update the copied fstab.

---

### Post by coffeecat on 2012-05-13
Copying a bootable system from one partition to another is possible with a simple file copy using cp, so long as you take account of these points:

1 - You need to preserve attributes as well as do a recursive copy. The -a option gives you all that = -p -d -R. Add the -v option to get feedback otherwise you will be sitting there for a long time wondering if anything is happening! :) This will do it:

```
sudo cp -av /media/old/* /media/new/
```

2 - You need to reset the UUID of the destination partition to match the original UUID of the source partition. You can do that with:

```
sudo tune2fs -U UUID <device>
```

Substitute the Actual UUID for "UUID" and presumably /dev/sdb1 for <device>. If you are still going to use the old sda3 and not reformat it, you'll want to change the UUID of that as well.

3 - If you don't reset the UUID, you'd have to edit both grub.cfg and /etc/fstab to match the new UUID, apart from re-installing grub to the mbr.

---

### Post by CatKiller on 2012-05-13
When I was doing similar, I used tar from a live cd.

---

