---
title: "Weird... formatting of storage drive wipes MBR?"
date: 2010-08-28
forum: General Help
---

### Post by BrandonBan6 on 2010-08-28
So I have a three drives on my machine. Main, Storage and Backup. 

If I re-format back-up, or seemingly if I touch the back-up drive in anyway (change the name, labels, etc)... at reboot I get the dreaded "No bootable devices insert a boot disk and press any key"

I've done this twice now, and each time I had to rebuild my system. 

Here's what I've ruled/figured out. 

It's not a BIOS issue, nothing in the boot order changed. 
The first time this happened, I was cloning an external drive to the back up drive with the Clonezilla live CD... I thought I hosed my MBR by ignorantly checking some random option in Clonezilla, so I re-installed Grub. Still no luck, I re-installed ubuntu. 

The second time this happened, I realized the backup drive needed formatted back to an XFS FS after I had used it to be a clone for the external. I used Gparted, ran the format, and upon the next reboot...same error. Again, ran through the community instructions to reinstall grub, but at reboot no change...same ugly error. I reinstalled ubuntu. 

Using Disk Utility, I can see all three drives right now. The 500 gb (backup)is an EXT4 FS. I'd like to rename the Label to "backup" and I also see it has a partition flag marked as bootable, which I would like to remove.

I'm afraid if I change the drive again, it will not boot up. Any thoughts out there? Does this make sense? What other info can I provide?

---

### Post by dcstar on 2010-08-28
> **BrandonBan6 said:**
> So I have a three drives on my machine. Main, Storage and Backup. 

If I re-format back-up, or seemingly if I touch the back-up drive in anyway (change the name, labels, etc)... at reboot I get the dreaded "No bootable devices insert a boot disk and press any key"

I've done this twice now, and each time I had to rebuild my system. 
........

And **exactly** where did you install Grub?

---

### Post by BrandonBan6 on 2010-08-28
> **dcstar said:**
> And **exactly** where did you install Grub?

I installed it to the main boot drive that has the OS. It didn't work, so I reinstalled Ubuntu completely. So I am back where I started, with three drives (main, storage, backup). I'd like to do so some fine tuning to "backup" (i.e. change label, it's flagged as bootable and I don't think it needs to be). However, I'm afraid it's going to cause my system to not boot again. Thoughts?

---

