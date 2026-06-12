---
title: "Force mount ntfs"
date: 2010-09-23
forum: General Help
---

### Post by kanbun on 2010-09-23
I am trying to read files on a hard drive that is damaged and will not boot.  The drive is on a Dell Inspiron running Windows 7.  Using a live CD I can run Ubuntu and the computer place shows the (OS) drive (250 mb).  However, attempts to view the drive contents returns and error code 13 and I cannot open the drive.  I have tried to force the drive open using "mount -t ntfs-3g /dev/sda1 /media/windisk -o force" and this doesn't work either.  I then used "fdisk -l" and see the contents of the drive - "sda1" which is the Dell utilities, and "sda2" and "sda3".  I substituted "sda2" and "sda3" in the force command, and was able to force open "sda2".  However, I cannot force open "sda3".

I am a novice at forcing open directories and would much appreciate any help with this.  It looks like "sda2" does not have any of the files I want, and it would be great if I can get into "sda3".

Thanks.
Kanbun

---

### Post by coffeecat on 2010-09-23
I should imagine that sda3 is your Windows C: drive. If the filesystem is damaged and will not boot then you need to fix it with Windows utilities. You risk damaging the filesystem even more by force mounting from Linux. NTFS is a Microsoft filesystem and Linux ntfs utilities are not comprehensive.

Do you have access to another computer running Windows 7? If so, you could try running chkdsk from that. Better still, you can download an ISO for a bootable Windows 7 recovery disc from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

There are both Vista and 7 discs available.

---

### Post by woodmaster on 2010-09-23
I used this when I had a corrupted filesystem on an external drive.  Hope it helps u.

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive")
[you-accidentally-wipe-your-hard-drive]("http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive")

---

### Post by kanbun on 2010-09-23
Don't have another Win 7 machine, but tried the recovery iso disc route and it doesn't recognize the drive.  So, I cannot run any recovery options since I can't get to them.  I assume this is because the hard drive is corrupted, but there must be a way to get at its content.

Will try the method posted by woodmaster and see what happens.  

Any further suggestions are appreciated.

Thanks.

---

