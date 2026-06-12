---
title: "got a new laptop, it came with 4 partitions, which one should i get rid of?"
date: 2012-02-28
forum: General Help
---

### Post by dan0804smith on 2012-02-28
so i got a laptop and it came with 4 partitions on it.  windows 7 os, hp recovery, hp tools, and system tools.
i already tried to install ubuntu through wubi, but it is buggy, so i want to dedicate a partition to ubuntu.   which one of these should i get rid of?  i am thinking hp tools, but is there any way to still keep this.   can i add it to the windows partition?

---

### Post by DeathShot on 2012-02-28
If they were smart OEM manufacturers would put most of these useless things in an extended partition but they don't. If you just got the computer I would say get rid of all of them and just keep windows. You really don't need the other ones, hp recovery is in case windows fails on you and assuming it still works it will install windows, I recommend you make a fresh windows install/repair CD and remove that one. I don't know what HP Tools is but you probably don't need it either, it's more OEM crap that will never be useful, less even if you dual boot linux and have an original windows DVD (which no doubt never came with your system, but windows 7 has the ability to make one).

The system partition is actually impotent for windows so don't get rid of it unless you have to, though I usually reinstall windows in an extended partition with both or them plus any data partition in it.

In short, just delete any HP crap that came with your computer and you will be fine ;)

---

### Post by grahammechanical on 2012-02-28
I have never done this and I no intention of buying a computer with windows 7 on it but

Is it not possible to transfer the files in HP tools and System tools into folders in the HP recovery partition? Or copy them to a DVD?

Of course it is possible to do this but could they still be used for the purpose that they were intended for? What ever that was.

Does anyone have a view on this?

Regards

---

### Post by DeathShot on 2012-02-28
> **grahammechanical said:**
> I have never done this and I no intention of buying a computer with windows 7 on it but

Is it not possible to transfer the files in HP tools and System tools into folders in the HP recovery partition? Or copy them to a DVD?

Of course it is possible to do this but could they still be used for the purpose that they were intended for? What ever that was.

Does anyone have a view on this?

Regards
They already come installed on your copy of Windows 7, those partitions are only there is you can't boot into windows. It's their way of saving money by not giving you a free windows DVD and insuring you always get all their OEM crap installed.

---

### Post by oldfred on 2012-02-28
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Someone posted that they backed up the HP tools and then restored to a new logical partition and they still worked. If you really want to keep them.

---

### Post by SeijiSensei on 2012-02-28
[Detailed instructions for installing Ubuntu on an HP]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5").

Warning:  You need to be comfortable with a command prompt to use the method I describe there.

---

### Post by dan0804smith on 2012-02-28
thanks all.  somtimes widows comes i handy so i need to keep the os.  i think i will back up the computer as a disk image and then induvidually back up the other smaller partitions.  i think i will just delete the hp tools for now. oh and i already burned a repair cd

---

### Post by Jerry N on 2012-02-28
I posted the following a few weeks ago:

[I]On my HP Mini 210 I:
1. Saved the folder in the HP-Tools partition
2. Used the Win 7 tools to delete the HP-Tools partition
3. Used the Win 7 tools to shrink the C: drive and create unallocated space (DO NOT use the Win 7 tools to create a new partition)
4. Used gparted to create an extended partition in the newly unallocated space and created an EXT 4 logical partition, a Linux Swap logical partition, and a 100mb Fat 32 logical partition.
5. Copied the folder saved from the HP-Tools partition to the new Fat32 logical partition.
6. Installed Ubuntu (in this case Linux Mint 9) in the EXT 4 logical partition.[/I]


Jerry

---

### Post by Mark Phelps on 2012-02-28
Some advice from experience ...

BEFORE you do the Win7 OS shrinkage, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will allow you to repair the Win7 boot loader -- should it become damaged during the dual-boot install.

THEN, after you shrink the Win7 OS partition, boot into it a couple of times to let the filesystem make any adjustments.

And finally, BEFORE you install Ubuntu, do the following:
1) Download and install the free version of Macrium Reflect into Win7
2) Start MR and use the option to image off the Win7 OS partition to an external drive.
3) Use the MR option to create and burn a Linux Boot CD.

At this point, you have (1) the means to repair the Win7 boot loader (from CD), and (2) the means to restore the Win7 setup (from backup).

So, if anything goes seriously wrong, you can get back to a working system with little effort.

---

