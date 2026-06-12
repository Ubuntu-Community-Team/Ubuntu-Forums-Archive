---
title: "suddenly out of disk grub rescue"
date: 2012-08-02
forum: General Help
---

### Post by waterhouse on 2012-08-02
Have Ubuntu 11.10 has worked fine for long time, suddenly boots to grub rescue with message error:out of disk. Have seen similar posts but these are usually after install or upgrade not out of blue. When at grub rescue prompt type ls I get (hd0,1) (hd0,msdos1). When type ls (hd0,1)/boot/ I get error: out of disk. When type ls (hd0,1)/boot/grub/ I get another error:out of disk. From different posts apparently system can't find grub folder but I don't know why this would be or what to do to restore it.

---

### Post by Kundan Negi on 2012-08-02
It seems your grub bootloader has crashed.You need make it correct or install the OS again.

---

### Post by waterhouse on 2012-08-02
How do I make it correct. I would like to get it running at least long enough to get data off my system before installing os.

---

### Post by HAPKAH on 2012-08-04
Hello!
I am having the same problem:
Lubuntu 11.10, no uptades, no any installations, cno changes, etc, system was starting fine for several past times. Only disconnected CD drive, but after that Lubuntu booted fine for a few times.

System is an old Celeron 433, with 20gb 2B010H1 Maxtor HDD and 192 MB RAM. Video is VIA or Intel, I'm not sure.

Then suddenly I got "out od disk \n grub rescue>". ls command gives exactly the same specified by TC.


I was able to boot only using Lubuntu 11.10 installation CD, choosing "boot from 1st hard drive".

NB! THIS HAPPENS 2nd TIME on this system, I already re-installed Lubuntu 11.10 after the same error.


HDD is detected by BIOS as ~10GB, LBA is supported.
I will try to reinstall grub as mentioned in this topic [http://askubuntu.com/questions/18531/error-out-of-disk-grub-rescue](http://askubuntu.com/questions/18531/error-out-of-disk-grub-rescue) and will try to resize ext4 20GB partition to something less than 8GB as recommended in some posts, but I'm not sure if it will prevent the problem from rising in the future.

Because last time GRUB crashed, it was installed on 128MB ext2 partition mounted as /boot.

There is some really mean bug in GRUB2.
I hope I've provided enough info. Please try to find and fix it...

Or advice some other boot manager. On much older linuxes, I remember LILO, which was able to boot to WinXP, RedHat ("
BestLinux" R2 or R3) and even boot to GRUB.

Is there any alternative to GRUB? (edit: to use with Lubuntu 11.10)

Edit: will use Hiren Boot CD to try resizing ext4 partition mounted at /.

---

### Post by drs305 on 2012-08-04
This can happen when your BIOS has a 137GB (or less) limitation on how much of the disk it can read. An update can move one or more of the critical boot files beyond the 137GB limit.

The solution is to 1) change your BIOS settings to enable large drives, 2) update your BIOS, or 3) create a /boot partition within the first 130GB or so of the drive.

You can first try the Boot Repair app's Advanced features (ATA disk support) to try to correct the issue. If that doesn't work, please run Boot Repair's info script and post the contents to confirm this is the issue. (Link in my signature line)

---

### Post by HAPKAH on 2012-08-05
The problem was that HDD is far below 137GB. Only 20GB to be precise.

I've used Parted from HirenBootCD 15.1 to shrink 20GB ext4 (mounted to /) partition to 7gb moved swap (230+ MB) rith after ext4 partition (to fit within first 8GB), will see if this helps...

---

