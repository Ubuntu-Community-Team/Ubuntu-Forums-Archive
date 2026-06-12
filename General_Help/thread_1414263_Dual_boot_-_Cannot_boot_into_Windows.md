---
title: "Dual boot - Cannot boot into Windows"
date: 2010-02-23
forum: General Help
---

### Post by mar387 on 2010-02-23
Hello all -

For some time now, I have had the dual boot option for Ubuntu and Windows 7.  Last night, in my daze of confusion at 4AM, I decided it would be smart to delete a small partition I created for Ubuntu through Windows 7.  I have just been way too busy to mess with Ubuntu due to school and I decided to delete this partition.  

Well stupid me did not realize that there must of been something important in order to boot from Windows on that 10GB partition, and now when I try to click on the Windows (Vista) boot, I get this error: "Error 12: Invalid device requested".  So I assume that I deleted the MBR or something along those lines.  I am able to boot into Ubuntu, 9.10, and see the data on my drive but I am not very familiar with the GUI version of Ubuntu; I have used Ubuntu 7.10 server at work.  

I have tried a disk repair, system recovery, etc but I realized that this isn't going to do anything.  I originally created this partition because when I originally installed Ubuntu, the default installation did not allocate a sufficient amount of hard drive space for the Ubuntu distribution and I was too much of a newb to not think of this.  I was trying to install test disk, since I saw good reviews about it but I can't even install it on my Ubuntu distribution because it says I don't have the space for it.  I tried installing it on the Windows 7 partition within Ubuntu, since I can see the data on there and its accessible but for some reason it doesn't, and I am guessing since it is formatted in NTFS.  


So is there anything I can do to fix this boot issue for Windows 7?  I am thinking at this point the most painless thing would be to back up all my data through Ubuntu and then just do a fresh install of Windows 7.  But I much rather try to get Windows 7 to work rather than doing that if possible.  Thanks for your time.

Regards,
Mike

---

### Post by ajgreeny on 2010-02-23
What you have probably done is remove all the configuration files for grub, but left grub on the MBR of your hard disk.  This means that though grub is still there and tries to boot, there is nothing for it to use as the grub menu, etc etc, hence the error message you see.

If you have a windows install disk you can repair the MBR with that, but probably a restore disk will not do the same.  However, failing that, download and burn a copy of Supergrub, which will also allow you to restore a windows MBR.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by mar387 on 2010-02-23
Thank you very much for your post.  I actually tried downloading super grub too.  My issue is, whenever I try to download something on the ubuntu distribution, I am informed I do not have enough space.  I have plenty of unallocated space on my HDD but for some reason when Ubuntu was installed it did not allocate a sufficient amount of space.  What can I do to increase the space on the Ubuntu distribution so I can actually install super grub?  

Also, where within the Windows 7 CD can I do a MBR repair?  Would I have to use the command line for that and could I possibly damage anything?  That is, if I even went that route.  Thanks.

---

### Post by mar387 on 2010-02-23
bump

---

### Post by PhoHammer on 2010-02-23
> **mar387 said:**
> Thank you very much for your post.  I actually tried downloading super grub too.  My issue is, whenever I try to download something on the ubuntu distribution, I am informed I do not have enough space.  I have plenty of unallocated space on my HDD but for some reason when Ubuntu was installed it did not allocate a sufficient amount of space.  What can I do to increase the space on the Ubuntu distribution so I can actually install super grub?  

Also, where within the Windows 7 CD can I do a MBR repair?  Would I have to use the command line for that and could I possibly damage anything?  That is, if I even went that route.  Thanks.

To enlarge an ubuntu partition and make room for super grub, boot your system with the Ubuntu Live CD. Then go to System menu, then Administration (I think) and Select Partition editor. Or just type sudo gparted in a terminal.

This will start gparted, a partition editor. You can then resize the Ubuntu partition as you see fit.

However, I think ajgreeny wants you to burn super grub on a disc, and use it like you would a Live CD.

---

### Post by ajgreeny on 2010-02-23
I only suggested supergrub because I suspected, maybe wrongly, that you don't actually have a windows7 install disk, just a recovery disk, which is what most manufacturers give you these days.  They seldom allow for the kind of repair I was talking about.

If you do have a windows7 install disk, boot from that and use whatever repair system that has to fixmbr.  I have no windows any more so can't help with the detail but I'm sure a google search will tell you what to do.  If you don't have a windows7 install disk, download the supergrub by whatever means you can, (a friend?) and burn it to a CD, boot from that and repair your windows MBR with that.

---

### Post by PhoHammer on 2010-02-23
> **ajgreeny said:**
> I only suggested supergrub because I suspected, maybe wrongly, that you don't actually have a windows7 install disk, just a recovery disk, which is what most manufacturers give you these days.  They seldom allow for the kind of repair I was talking about.

I agree that this is common, even my laptop that came with Vista simply had the "reinstallation" partition. Not even an installation *or* recovery disk. Not sure why they do this, maybe to save them money on disks and use up our valuable HDD space...:)

---

### Post by v1ad on 2010-02-23
so whats the problem?

---

