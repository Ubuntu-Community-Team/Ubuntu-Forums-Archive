---
title: "running   out of space , how  to extend my current ext3 partion ?"
date: 2010-02-16
forum: General Help
---

### Post by rahul23 on 2010-02-16
I had initially created 10 GB ext3 partiton for my kubuntu 9.10 , but now space is almost full , I tried Gparted
but it wont let me unmount my ext3 partition ?
The error is posted below.
I got windows 7 on another partition but its partition manager does not support ext3 so its useless ??
shd i boot from live CD and then extend my partition or is there an easy way out , like using "parted" command line tool ??

Thanks in Advance.

> 
Could not unmount /dev/sda2

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.


---

### Post by oldos2er on 2010-02-16
Yes, boot from the LiveCD and run gparted from there. You can't unmount / when you're booted from it.

---

### Post by byStanderone on 2010-02-16
...is it correct to say that you have two existing partitions, (3 if swap is counted),,,ubuntu is in ext3, while win7 in ntfs? should your windows partition be in ntfs, you'll have to install your ntfsprogs in your ubuntu for gparted to be able to work on an ntfs job.

note: be sure to boot on your win7 first, right after any re-sizing using ubuntu gparted,so as to allow window to update its data. and remember to backup your important files before manipulating your hdd.

---

### Post by rahul23 on 2010-02-18
@thanks all

I will make a live cd and boot from it and then extend my existing ubuntu ext3 partition, which will get hardisk space from windows ntfs partition , hope everything works after the opertion since i cant make backup of 1TB .

---

### Post by rahul23 on 2010-02-18
> **rahul23 said:**
> @thanks all

I will make a live cd and boot from it and then extend my existing ubuntu ext3 partition, which will get hardisk space from windows ntfs partition , hope everything works after the opertion since i cant make backup of 1TB .

I extended my partition successfully through gparted in the live CD , but now the GRUB is not loading , only windows loader is loading windows 7 , there is no sign of grub , how do i boot my kubuntu ???

Thanks in advance

---

### Post by byStanderone on 2010-02-21
...you have to install grub from your live cd.

---

