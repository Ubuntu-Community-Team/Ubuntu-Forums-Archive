---
title: "Remove fake drives spaces in their names from /media"
date: 2011-11-05
forum: General Help
---

### Post by dez93_2000 on 2011-11-05
To remove a 'ghost' drive with, for example, an underscore at the end one does this:

> sudo rmdir /media/hddNamedoes anyone know how to do this for drives with spaces in their names? I  have two drives like this. The first, for example, is called '80gb OldC' but shows up in /media as
80gb OldC AND
80gb\040OldC and used to also show up as
80gb OldC_ which had the drive contents recursed below it, however these  drives have both vanished. I can mount them in 'disk utility', however,  so i'm not too worried about them yet.

My problem is that I can't remove the entries for the false named drives, and until I remove '80gb OldC' I can't mount the actual drive or it'll be called '80gb OldC_' and thus all my links & shortcuts won't match up.

I've tried copying the name after listing the directory in terminal, as  well as typing it out, but neither works. Any assistance gratefully  received. Thanks!

---

### Post by gsmanners on 2011-11-05
???

You mind doing a:

```
sudo blkid
```

and copy/paste the output? Not quite sure what the problem is.

---

### Post by dez93_2000 on 2011-11-05
I don't mind at all.

/dev/sda1: LABEL="SamsungA" UUID="8E3CDEC53CDEA80B" TYPE="ntfs" 
/dev/sdb1: UUID="9dcff44a-8d21-42c6-978c-a3685b520855" TYPE="ext4" 
/dev/sdb5: UUID="79c91a3a-979a-411f-a192-d1e44c7d37f6" TYPE="swap" 
/dev/sdc1: LABEL="80gbOldC" UUID="82A47E73A47E6A15" TYPE="ntfs" 
/dev/sdd1: LABEL="120gbAltBoot" UUID="F0F02DA2F02D6FD0" TYPE="ntfs" 
/dev/sde1: LABEL="Thanatos" UUID="D680869080867731" TYPE="ntfs" 

But what i really mean is:
[IMG]http://s9.postimage.org/6ggwu3cmn/image.jpg[/IMG]
I want to delete these entries then i'll re-mount sdc1 & sdd1 in the list above. I already did this with dupes of 2 other drives which didn't have space bars.

---

### Post by gsmanners on 2011-11-06
That's very strange, but maybe Nautilus is confused by the fact that those drive labels start with numbers rather than a letter.

---

### Post by dcstar on 2011-11-06
> **dez93_2000 said:**
> To remove a 'ghost' drive with, for example, an underscore at the end one does this:

does anyone know how to do this for drives with spaces in their names? I  have two drives like this. The first, for example, is called '80gb OldC
.....

As with **everything** with a space, simply enclose it in quotes.

BTW, have you been putting these removable dives in /etc/fstab, this is the sort of issue that occurs when people do this?

---

### Post by dez93_2000 on 2011-11-06
Top prize to David - thanks for that. Thanks also gsmanners - quite probably the reason behind it.
David - these aren't removable drives (well, technically the are since i've not glued them in, but they're IDEs which should mount at startup). I'm pretty sure it was caused when I repair installed over the top of an 11.10 install which would no longer boot.

Cheers all!

---

