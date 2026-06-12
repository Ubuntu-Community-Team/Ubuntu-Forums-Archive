---
title: "Ubuntu Livd CD to restore Vista winload.exe ?"
date: 2010-03-23
forum: General Help
---

### Post by Trvlr on 2010-03-23
[SIZE=5][COLOR=Blue]My Vista booting files are busted.
Windows Boot Manager says: ...winload.exe missing or corrupted.

Have read an article saying that Ubuntu Live CD can restore winload.exe or MBR.
I am an apprentice and unable to carry out such a complicated task.

Ubuntu Live CD 8.10 or 9.04 is on hand.

Please help.

Thank you![/COLOR][/SIZE]

---

### Post by lindsay7 on 2010-03-23
Download and burn this to a disk.  Run the repair option first and see if that fixes it.  If not post back for more help.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by Sdream on 2010-03-25
> **lindsay7 said:**
> Download and burn this to a disk.  Run the repair option first and see if that fixes it.  If not post back for more help.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Thank you, Lindsay7 !

I know this repair tool and have it in PC.

My hope is to fix the Vista winload.exe by Ubuntu Live CD so that I may learn Ubuntu.
Have tried Ubuntu Live CD and gotten into the Rescue Mode but not found what that author said. This is what roughly what that author said:
1. Run Linux Live Cd and enter Rescue.
2. Connect to internet and keep it connected.
3. Input these commands . . . ( I do not remember the commands)
The effect is the same as fdisk\fxmbr.

Is Ubuntu Live CD having the same function as what the author said?

Thanks!

---

### Post by Mark Phelps on 2010-03-25
> **Trvlr said:**
> [SIZE=5][COLOR=Blue]My Vista booting files are busted.
Windows Boot Manager says: ...winload.exe missing or corrupted.

Have read an article saying that Ubuntu Live CD can restore winload.exe or MBR.


You can not repair the Vista boot loader with Ubuntu CDs.  There are some other CDs you can use to overwrite the MBR, but they won't repair the boot loader.

Lindsay7 provided you the link to where you can download the Vista/Win7 Repair CD images.  You need to burn the one(s) you need to CDs.

Also, you need to select Startup Repair and run it three times.  It only repairs one problem per pass, and repairs the MBR on the third pass.

---

### Post by Sdream on 2010-03-25
> **Mark Phelps said:**
> You can not repair the Vista boot loader with Ubuntu CDs.  There are some other CDs you can use to overwrite the MBR, but they won't repair the boot loader.

Lindsay7 provided you the link to where you can download the Vista/Win7 Repair CD images.  You need to burn the one(s) you need to CDs.

Also, you need to select Startup Repair and run it three times.  It only repairs one problem per pass, and repairs the MBR on the third pass.

Thank you very much, Mark Phelps !

Maybe you are right.
That author did not mention Ubuntu, but  Linux Live CD  like KNOPPIX or similar . . . 
Maybe this is why I do not find what that uathor said in Ubuntu Live CD.

Thank you very much again, Mark Phelps !  Really appreciate !

---

### Post by Sdream on 2010-03-27
> **Mark Phelps said:**
> You can not repair the Vista boot loader with Ubuntu CDs.  There are some other CDs you can use to overwrite the MBR, but they won't repair the boot loader.

Lindsay7 provided you the link to where you can download the Vista/Win7 Repair CD images.  You need to burn the one(s) you need to CDs.

Also, you need to select Startup Repair and run it three times.  It only repairs one problem per pass, and repairs the MBR on the third pass.

Hi, Mr. Mark Phelps:

What you have said can not be found in Lindsay7 but ads and . . . .
Will you please give a bit more details?

---

### Post by Mark Phelps on 2010-03-27
> **Sdream said:**
> Hi, Mr. Mark Phelps:

What you have said can not be found in Lindsay7 but ads and . . . .
Will you please give a bit more details?

Then you didn't read the whole thing ...

The link provided takes you to a page that has three download links in it -- in the light green boxes.  You have to follow the directions and install a bit torrent client in order to use these links.

---

