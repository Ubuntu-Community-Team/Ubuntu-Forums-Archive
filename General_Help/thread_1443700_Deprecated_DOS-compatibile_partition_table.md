---
title: "Deprecated DOS-compatibile partition table"
date: 2010-03-31
forum: General Help
---

### Post by Arch Linux on 2010-03-31
I know it's just a warning, but how can I remove the compatibility?
```
&#9484;&#9484;(det@Archlinux)-(09:08pm-:-03/31)&#9484;-¨-¨¨&#729;
&#9492;&#9484;(~)&#9484;¨&#729; sudo fdisk /dev/sda

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help):
```

---

### Post by Arch Linux on 2010-04-01
o_O

---

### Post by Chronon on 2010-04-01
> **Arch Linux said:**
> I know it's just a warning, but how can I remove the compatibility?
```
&#9484;&#9484;(det@Archlinux)-(09:08pm-:-03/31)&#9484;-¨-¨¨&#729;
&#9492;&#9484;(~)&#9484;¨&#729; sudo fdisk /dev/sda

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (***command 'c'***) and change display units to
         sectors (command 'u').

Command (m for help):
```

Did you read the output that you posted?

---

### Post by Arch Linux on 2010-04-01
I red the other part too (which you didn't.. also, you are supposed to actually write the changes too) but the thing is that it won't matter, if I do this even with Live-CD.

---

### Post by hangfire on 2010-04-01
Well... you can delete the entire partition table and then recreate it. Fine for a new disk or one with absolutely nothing important on it.

-HF

---

### Post by Arch Linux on 2010-04-01
But that's not so practical solution because my HD is almost full and is 500gb in size =).

---

### Post by GepettoBR on 2010-04-01
Changes to the partition table are risky business. You should assume that your data will be destroyed. So, either ignore the problem or back up all your data before fixing it.

---

### Post by pbrane on 2010-04-01
As GepettoBR says partition table changes can be risky. However in this case you are only toggling the DOS compatibility flag. You *should* be able to change that without issue. If the other partition data stays the same then you shouldn't loose any data. Having said that, you **really should** research this further and backup your data before trying it.

---

### Post by srs5694 on 2010-04-01
I'm pretty sure that the "DOS compatibility flag" in fdisk is entirely in-program. That is, fdisk doesn't write anything to the partition table to indicate that it's "DOS compatible." What toggling those two items ('c' and 'u' on the main menu) does is to enable you to enter partition start and end points in a sector-exact way and, with the very latest versions, sets a minimum first sector value of 2048 rather than 1 or whatever the number of sectors per cylinder is (usually 63). If I'm right about this, there's no need to set this mode on existing disks unless you intend to add new partitions to it. Even then, Linux doesn't really care one way or another. Setting DOS-compatible mode is important for some older OSes, such as DOS and (so it's claimed) Windows up through Windows XP; these OSes don't react well to partitions that begin mid-cylinder, by CHS geometry standards. Windows Vista and Windows 7 create partitions that begin with sector 2048, but AFAIK they can still handle disks that are partitioned in the older way. The newer method has performance advantages on RAID 5 and 6 arrays and on a few new hard disks with 4096-byte physical sectors, such as some new Western Digital Caviar Green models.

---

### Post by Chronon on 2010-04-01
It does have an effect on the partition table, apparently:
> If the flag is set, then partitions starting/ending above cylinder 1023
have their cylinder set to 1023 in the partition table. If it isn't
set, the cylinder is set to (cyl % 1024).

Parted's behaviour always matches fdisk's "dos compatibility flag"
behaviour. I am not aware of any reasons why you would ever not
want to behave like this. libparted has no option to "disable" this
behaviour.

from [http://osdir.com/ml/gnu.parted.bugs/2004-08/msg00044.html](http://osdir.com/ml/gnu.parted.bugs/2004-08/msg00044.html)

Arch Linux: If you have that much data on it and Linux is working okay, I would probably ignore it.  How was the partition table created in the first place, out of curiosity?

---

### Post by srs5694 on 2010-04-01
I just confirmed that unsetting "DOS compatibility" mode causes the weird (cyl % 1024) value to be used in the cylinder field. This is very peculiar. I've never heard of such behavior before. (Windows Vista doesn't do this; I just checked.) This sounds like a bug to me, although I'm not positive of that. In any event, when the cylinder number is over 1023, the CHS addressing values are useless; the system should use LBA addresses exclusively. Thus, this difference in what's written to disk should make no difference in the real-world performance of modern OSes or disk utilities, with one caveat: If a program checks for maxed-out CHS values as a cue to use the LBA values, then this new behavior in fdisk will cause problems. I don't know if any real-world tools use such a test, though.

---

### Post by Arch Linux on 2010-04-03
Okay then. Wonderful community even though I don't like Ubuntu itself so much. Thanks for everybody, marking as [Solved].

---

### Post by alecz20 on 2011-12-27
So what is the solution? I tried command 'c' then command 'u' then 'w', but the warning reappears. This is a freshly formatted drive - so no data now.

---

### Post by oldos2er on 2011-12-28
> **alecz20 said:**
> So what is the solution? 

Finding a solution involves starting a new thread, since this one is going on two years old. And please give as many details about your problem as possible.

Closed.

---

