---
title: "De-installation questions"
date: 2006-06-19
forum: General Help
---

### Post by link141 on 2006-06-19
Hey guys.
Say you partitioned your hard-drive into with Ubuntu and Windows on it, and you decide to uninstall Ubuntu.  How would you be able to **completely** remove **all** of the components that were necessary to run Ubuntu with Windows on the same computer (Ubuntu data, Grub).  Will deleting the Linux partitions take care of that, or is there some extra procedure one must follow in order to accomplish this?  If so, how would one go about this?
Thanks to all.

---

### Post by bruce89 on 2006-06-19
You'd have to delete the partitions and use the recovery mode of the windows CD to install the MBR again.  Of course, you should then resize the windows partiton up again.  Why are you going?

---

### Post by glotz on 2006-06-19
Remove the partitions and overwrite MBR.

Use fdisk, partition magic or something. Start windoze CD > repair mode > fixmbr.

---

### Post by Ocxic on 2006-06-19
deleting the partition will erase all of ubuntu data. how ever this will not remove grub. to remove grub boot with your windows cd, and go into recovery mode and type "fixmbr" reboot, and your done.

you will have to find a tool to resize your drive back to normal, as simply deleting ubuntu's partiton will not return your freed space to windows. 

alternativly you could just format ubuntu's partiton and have a seperate drive in windows for storage, wich can be done by right clicking My computer-->manage and in the right hand list select disk managment. just make sure you pick the correct drive/partition.

---

### Post by link141 on 2006-06-19
Thanks guys,
Can I ask something, what is the MBR?  Also, will I have to re-activate Windows after using the fixmbr command, those dorks are paranoid about piracy.  

I was going to "sneak" Kubuntu on the other computer in my house (for network compatibility, testing, and others), and wanted to know if I could return it to it's original state in case something went wrong.  I am going to use the G-parted live-CD if I decide to do this.  It seems that doing this will work more cleanly than I originally anticipated. 
thanks

---

### Post by Kyle- on 2006-06-19
"MBR" -> "Master Boot Record"  

In a nutshell, the MBR is a small bit of code at the beginning of your harddrive that tells your computer what partition/kernel to boot from.  

You will not have to reinstall or reactivate Windows after reinstalling the MBR.  

It's really a pretty painless procedure if you follow the directions people gave above.  The actual writing of the MBR takes about one second.  

Good luck,

Kyle-

---

### Post by link141 on 2006-06-19
Thanks Kyle-.  :) Ubuntu Linux will rule my house!!

---

### Post by mzracer360 on 2006-06-29
Im sorry if im bumping an old topic...

I too am wanting to remove Ubuntu and all of its components.  I have always wanted to try Linux, and when I found out about Ubuntu, I thought Id give it a shot.  I enjoyed learning LInux, but found that I can't do things that I could do with Windows (i.e. Gaming.)  I do not have an actual Windows cd to use to fix the MBR, instead, I have a recovery cd that came with my Toshiba.  Is there any other way of fixing the MBR without the WIndows cd?

---

