---
title: "Will lost+found folder still work if I make it hidden?"
date: 2009-08-23
forum: General Help
---

### Post by Brionius on 2009-08-23
I recently added an internal hard drive to my system, and I reformatted and mounted it successfully.   gparted created the "lost+found" folder on the drive, which, as I understand it, is used by the system to dump active files in case of a messy system shut down.  However, I'd kind of like to make the lost+found folder hidden, so the drive looks cleaner, so only the folders I create appear.  My question is this:

If I execute the following command

mv lost+found .lost+found

will the lost+found folder still be used in the event of a system crash?  Thanks in advance for your help!

---

### Post by michy99 on 2009-08-23
If the system needs a lost+found folder and it does not exist, it will create one. If you rename it, the system will create a new one if it needs to. Better to just delete it.

---

### Post by Brionius on 2009-08-23
> **michy99 said:**
> If the system needs a lost+found folder and it does not exist, it will create one. If you rename it, the system will create a new one if it needs to. Better to just delete it.
Even better - great - thanks!

---

### Post by CatKiller on 2009-08-23
For reference, if there's something that you don't want to rename, but you just don't want to see it in the file manager, you can create a text file in that directory called **.hidden**. Put the names of any files or folders in the same directory in this file, one per line, and they will not be shown by the file manager, along with files that start with **.** or end with **~**.

---

