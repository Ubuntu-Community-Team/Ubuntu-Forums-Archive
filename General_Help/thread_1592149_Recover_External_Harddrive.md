---
title: "Recover External Harddrive"
date: 2010-10-10
forum: General Help
---

### Post by emoguitarist06 on 2010-10-10
I have an external 250GB Seagate Harddrive and it gives me this error when I plug it into my Ubuntu Machine

[IMG]http://i1203.photobucket.com/albums/bb398/phillipguy/Screenshot-UntitledWindow.png[/IMG]

and here is a Gparted picture of the partitions on it

[IMG]http://i1203.photobucket.com/albums/bb398/phillipguy/Screenshot--dev-sdb-GParted.png[/IMG]
[COLOR="Red"][B]
How can I recover the files from the NTFS partition?
Also the NTFS partition is not bootable[/B][/COLOR]

---

### Post by coffeecat on 2010-10-10
The answer to your problem is in the error message. You will have to plug the drive into a Windows machine and run chkdsk. There are no Linux tools that will be able to fix it. The comment about rebooting twice is for if the NTFS partition is a Windows C: drive. Which yours isn't, but you still need to run chkdsk.

---

### Post by emoguitarist06 on 2010-10-11
YUP

Just decided to run DBAN and wipe it ;)

---

### Post by coffeecat on 2010-10-11
> **emoguitarist06 said:**
> Just decided to run DBAN and wipe it 

Unless you had sensitive data that you wanted to make completely unrecoverable, that was a complete waste of time. You could have simply reformatted it in Gparted which would have taken seconds, instead of dban which probably took hours.

The days of having to zero out or shred a drive when you format it belong firmly in the past - 1995 or thereabouts.

---

### Post by emoguitarist06 on 2010-10-11
> **coffeecat said:**
> Unless you had sensitive data that you wanted to make completely unrecoverable, that was a complete waste of time. You could have simply reformatted it in Gparted which would have taken seconds, instead of dban which probably took hours.

The days of having to zero out or shred a drive when you format it belong firmly in the past - 1995 or thereabouts.

You know what? **Thanks**I didn't even think about using Gparted to format the drive. It was actually my friends external so I'm not sure if it had anything sensitive but oh well eh? But I'll remember this for next time!

---

### Post by Andrew.Z on 2010-10-22
> **coffeecat said:**
> Unless you had sensitive data that you wanted to make completely unrecoverable, that was a complete waste of time. You could have simply reformatted it in Gparted which would have taken seconds, instead of dban which probably took hours.

The days of having to zero out or shred a drive when you format it belong firmly in the past - 1995 or thereabouts.

You seem to be referring to Peter Gutmann's 1996 paper on wiping drives with 35 sequences (to prevent recovery using microscopy), the evolution of MFM interfaces to IDE around 1990, and constantly increasing HDD densities.  While it's true that [exactly one pass is enough](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk) (with zeroes or any other pattern), what you are describing with gparted erases only the partition table and leaves the file system intact.  That means it wouldn't be difficult to find the file system and recover all the files.  I recommend using DBAN or linux command 'dd' to overwrite the entire disk (not just free space) with a single pass.  If it is sensitive, make sure DBAN overwrites the remapped bad sectors.

---

### Post by coffeecat on 2010-10-22
> **Andrew.Z said:**
> You seem to be referring to Peter Gutmann's 

Nope. I was thinking of the hours and hours you can waste with dban when you don't need secure deletion. I think you've interpreted my thinking the wrong way round.

Although, now you mention it, I seem to remember Gutmann's was one of the options that dban offers you. That and a tin-foil hat no doubt!

I see that even the terminal utility shred has now reduced its previous default of 25 passes down to 3.

> **Andrew.Z said:**
> what you are describing with gparted erases only the partition table and leaves the file system intact.

I am well aware of that. That is probably all the OP needed, because once he had created new partitions and new filesystems the old filesystems became an irrelevance.

---

### Post by ssdt on 2010-10-23
Is there no software to hold my backup? I have a 1 Tb with lots of files which I want to be able to recover but how is it possible?

---

