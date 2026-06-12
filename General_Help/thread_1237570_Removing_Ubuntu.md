---
title: "Removing Ubuntu"
date: 2009-08-11
forum: General Help
---

### Post by Maxcore on 2009-08-11
Hello, I have Ubuntu installed of one of two hard drives in my computer. I am running out of space on my windows hard drive and now need to remove ubuntu from my other one to free up some space. How can I safely remove ubuntu so that GRUB and Ubuntu are both gone and my computer boots up my windows partition every time?

---

### Post by Buuntu on 2009-08-11
You need to first uninstall Ubuntu form the Live CD. Go to System > Administration > Partition editor. You should also remove the swap (if any).
 
Then you need to use your windows install disc and boot from it. Change the BIOS preferences so the CD boots before the hard drive.
 
Once the CD boots you need to enter the recovery console (try R, but it should say what to press). From there type ```
fixmbr
```
That will write a new boot record to your hard drive.
Quit and restart.  It should go straight to Windows.

---

### Post by adempewolff on 2009-08-11
I would get a second opinion before you do this as I'm not 100% sure it will work and haven't done it in a while but:

For XP: use your xp cd and boot into the windows recovery console--not "automated system recovery" (press r while it is starting up I think... just pay attention while it is booting and it will tell you what button to press).  Once it loads and you get a command prompt type "fixmbr" and then "fixboot".  This should remove GRUB from the mbr and make xp boot by itself.

For Vista: On your Vista DVD there is an option called "Startup Repair" that should do the ticket.

Once you have removed GRUB from the MBR and made your windows os bootable then use gparted from a live cd to delete your ubuntu partition and expand the ntfs partition over it.  make sure to back up all your data before you do this.  Editing partitions always has the potential for data loss.


Once again I am not completely sure if this method will work and obviously do not remember all the exact buttons to press etc.  I would wait until a more knowledgable user posts a method.  If you don't get any more hits though I will refresh my memory and try and help you.

edit: the above guy's method looks solid and is much more user friendly.  I personally though would make windows bootable before deleting ubuntu so if the fixmbr fails GRUB can still find stage 2 (which is on your ubuntu partition) and boot you into windows.

---

