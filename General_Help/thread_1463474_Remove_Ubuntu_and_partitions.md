---
title: "Remove Ubuntu and partitions"
date: 2010-04-27
forum: General Help
---

### Post by mkhall49 on 2010-04-27
Hello,

I've been searching through the forums for information on removing Ubuntu, but all of the posts with detailed information seem to be very old.  Can someone reply with up to date instructions on how to completely remove Ubuntu without needing to reinstall Windows?  I am using Windows 7 Professional and Ubuntu and I need the space.  Thank you!

---

### Post by bcbc on 2010-04-27
You want to reinstall the windows boot loader to the MBR of the disk. See [here]("http://ubuntuforums.org/showpost.php?p=6391959&postcount=1") or [here]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"). 

Then you can just open up disk management in windows and delete the ubuntu partitions from there.

---

### Post by Mark Phelps on 2010-04-27
> **mkhall49 said:**
> I am using Windows 7 Professional and Ubuntu and I need the space.  Thank you!

Since you can boot into Win7, if you haven't done this already, go into the Backup function, create and burn a Win7 Repair CD.  You can then use that to restore the MBR.

---

### Post by mkhall49 on 2010-04-27
I have not tried it yet, but I want to make sure I understand before I make an attempt.  This sounds like it removes the boot program so that Windows automatically loads, but does it remove all the partitions as well?

---

### Post by bcbc on 2010-04-27
No - it does not remove the partitions.

Right now you have grub as your bootloader. You computer starts up, bios looks in the MBR of your harddrive and finds grub. Grub points to your ubuntu partition and pulls the boot menu you see.

When you replace the MBR with the windows bootloader, instead it will look on the partition marked active and then find the windows 7 boot files and load windows 7.After replacing the MBR you will not be able to boot ubuntu, but the partitions will still be there untouched.

To recover the space used by ubuntu, you can either reformat those partitions as ntfs and then use them from windows 7, or delete them and merge them with your windows partition. You should do all this from the Windows 7 disk management tools.

If you need to backup anything, do it first from ubuntu as windows won't be able to see the files.

---

