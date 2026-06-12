---
title: "dual boot problem"
date: 2010-01-08
forum: General Help
---

### Post by londis52 on 2010-01-08
Hi everyone. 

My Dell Inspiron 545 MT won't boot into either operating system - 64 bit Ubuntu 9.10 and Windows 7.  I'd appreciate some advice before I start messing about with the live CD.  Perhaps grub or grub.cfg  is corrupt and can be repaired?  Maybe I'd be better off restoring the factory image and starting again?  I'm a linux newbie and would like to continue dual booting for a while.

Error message is:  
Boot from CD
Grub loading
The symbol 'r' not found
Aborted. Press any key to exit.

Both operating systems seemed to be working correctly until yesterday when I booted into Windows.  It complained about a disk problem and asked me if I wanted to run check disk.  I said yes, and Windows started up normally. Today the PC won't boot .

I've downloaded all the Ubuntu updates and also the proprietary driver for the GT220 video card.

A few days ago,  Ubuntu update asked me 'what would you like to do about grub'.  Did I want to keep the current version because it had been locally modified.  (Presumably because I set the keyboard and local time to UK).  I said keep the current version - which may have been a mistake?

Thanks for your time.

---

### Post by Leppie on 2010-01-08
you can easily restore grub2 with the livecd.
boot with the karmic livecd, then open a terminal and issue this command and post the output:
```
sudo blkid
```

---

### Post by londis52 on 2010-01-08
Thanks, the output was:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0C16" TYPE="vfat" 
/dev/sda2: UUID="68B2B214B2B1E72A" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="7ECEB509CEB4BAAB" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="4e2096d0-ee5a-43ec-8288-d847301b4f49" TYPE="ext4" 
/dev/sda6: UUID="d3d840bf-6431-4ad6-889d-2687f0e5c369" TYPE="swap" 
/dev/sdf1: UUID="01C8974BC300A580" LABEL="MyPassport2" TYPE="ntfs"

---

### Post by Leppie on 2010-01-08
still booted with the livecd, issue these commands to restore grub2:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

then reboot

---

### Post by londis52 on 2010-01-08
Thank you so much.  I was able to start Ubuntu and all seems well. 

Do you have any idea where it all went wrong?  Should I ignore Window's requests to run check disk in the future, or was it something else?

Thanks again - you've saved me hours of messing about!

---

### Post by Leppie on 2010-01-08
i'm not sure what went wrong, do you normally use ubuntu and windows only once in a while?

---

### Post by Leppie on 2010-01-08
i'm glad you can use your system again :)

---

### Post by londis52 on 2010-01-08
Yes, I tend to use Ubuntu most of the time and hope eventually to move 100% to Ubuntu.  My PC is new and came with Windows 7, so I'm a little bit curious about it.  Don't think I'll bother learning too much about it though.  I don't see what all the fuss is about.

If I have time I may re-install everything again, and this time choose the default (US) settings during installation, and  let Ubuntu update the grub.cfg file.  Oh, and make an image of disk.

---

