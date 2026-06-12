---
title: "Using Super Grub Disk"
date: 2010-01-21
forum: General Help
---

### Post by cdy on 2010-01-21
Hi. I installed Ubuntu and grub on my sony laptop over a year ago.  I need to remove ubuntu and perform a windows recovery using the supplied disks. It is my understanding that I need to run the supergrubdisk to fix the mbr before I do this.  I just wanted to verify that I was doing this correctly.
Download this iso [super_grub_disk_0.9799.iso]("http://prdownload.berlios.de/supergrub/super_grub_disk_0.9799.iso") and burn it to a disk normally.
Put the disk in and restart computer.
Follow menus and fix the mbr.
Delete ubuntu partitions since no longer needed.

Is this correct?

Thank You for your help.

---

### Post by cdy on 2010-01-22
Anyone?

---

### Post by 73ckn797 on 2010-01-22
If you have your Windows disk boot from it and go to recovery (pressing r when you get to the menu). Once the command prompt comes up enter ```
fixmbr
``` and that will fix things.

Super Grub Disk will also have a choice to do the same.

You can delete the partitions using the Ubuntu LiveCd by booting from it and running the first menu choice. Once loaded go to System/Administration/Gparted where you can delete partitions and resize them to suit.

---

### Post by cdy on 2010-01-22
Thanks for your reply.  I would use a windows xp disk but the computer only came with recovery disks.  I guess I will proceed with super grub.

---

### Post by 73ckn797 on 2010-01-22
> **cdy said:**
> Thanks for your reply.  I would use a windows xp disk but the computer only came with recovery disks.  I guess I will proceed with super grub.

That will be your best bet.

If you have any earlier Windows disk you may be able to perform the same "fixmbr" function. I have used a Millenium disk to do it with.

---

### Post by cdy on 2010-01-22
Ok. So I burned the ISO to the disk and it works fine.  Then I found the options to fix the windows boot.  I press enter and it gives me an option for "syslinux" after I select that I see my hard drive.  Is this what I should be given? I was expecting it to say windows xp not syslinux.

Sorry for all the questions. I just want to do this right.

Thanks,
cdy

---

### Post by 73ckn797 on 2010-01-22
Exactly what did you select when using SGBD? There is a choice for Windows.

Have you tried running the command to "fixmbr" from within Windows? Try using the command prompt.

---

### Post by cdy on 2010-01-22
I chose fix boot for windows, (or something similar) and it gave me the option of syslinux. Is this what fixes the MBR?

---

### Post by meierfra. on 2010-01-22
> Is this what fixes the MBR?
Yes.  That's was  Super Grub uses for fixing the MBR. It's different when the regular Windows MBR, but does the same thing: Load the code in boot sector of the active partition.

---

### Post by cdy on 2010-01-22
Cool.  One more question... You say that its different but does the same thing.  So that means after I do this, my recovery disks should still recognize my xp os. Right??

Thanks, 
cdy

---

### Post by meierfra. on 2010-01-22
> So that means after I do this, my recovery disks should still recognize my xp os. Right??

Yes (at least I have never seen  case the a case where it didn't)

---

### Post by 73ckn797 on 2010-01-22
> **meierfra. said:**
> Yes (at least I have never seen  case the a case where it didn't)


Yes, same here.

---

### Post by cdy on 2010-01-23
Thank You both.  SGD worked great. So did my recovery disks.

---

