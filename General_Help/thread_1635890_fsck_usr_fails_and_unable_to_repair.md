---
title: "fsck usr fails and unable to repair"
date: 2010-12-02
forum: General Help
---

### Post by surferX on 2010-12-02
My usr partiition has failed, I cant fsck it because the sudo command seems to be usr...

I am travelling so would really appreciate a few tips that should hopefully get my pc running again. (I have internet access via a kiosk, and can burn a disk if necessary, but the smaller the download the better)

I have a few ideas that with some help I should be able to fix the partition.

1. Is there a simple way to use use grub, to mount all partitions read only and not to fsck them so I can logon in normal user and sudo and hopefully fix the parition?

or 

2. Download a small version of ubuntu or something that I can burn to CD (my machine cannot boot from usb) so that I can repair the machine.

3. Download the ubuntu installer (alternative) and try and reinstall the necesary usr partition?

Appreciate any tips!!!

---

### Post by Herman on 2010-12-02
You can use a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), it's a 123.9 mb download for the latest release, GParted 0.7.0-4
It contains GParted plus a small collection of other extremely useful softwares.

Or you can use [Parted Magic]("http://partedmagic.com/"), which also contains GParted plus a [larger collection useful programs and software]("http://partedmagic.com/programs.html"), notably Super Grub Disk and many others, but it's still only a small download, about 144 mb.

Either of those should be ideal for your needs.  :)

---

### Post by surferX on 2010-12-03
Thanks for that!!!!

[LEFT]Tried  [Parted Magic]("http://partedmagic.com/")but the cd image does boot on my machine, perhaps a bios problem, I will give gparted live cd a shot now (It takes over an hour to download 144mb). I see that it has an editor so as long as it boots I should be able to modify the files in etc. 

One more question, if was planng on changing etc/fstab to mount everthing ro, but is there a simple way to boot ubuntu so that all partitions are mounted ro and with just a command prompt (dont start xwindows etc) and NO fsck of the file systems, so I can try and fix my laptop?
[/LEFT]

---

### Post by endotherm on 2010-12-03
well the very first thing you probably want to do is check the smart data on the drive to ensure that it is mechanically healthy. if the drive is starting to fail, recovery will just make a bigger mess, and can ultimately result in damage to your other partitions (crashes can lead to failed dismounts, which can lead to filesystem corruption or even mechanical damage). if the drive is not healthy, replace it asap. 

you can reboot in recovery mode (single user; rc3 iirc) to get a minimal shell as root, but you don;t want to run fsck or any other partition recovery software while the drive is mounted, even as RO (since it can't fix anything on an RO partition without remounting as rw).
you can get to recovery mode from the grub menu if you hit esc during grub load.

I would probably boot from a ubuntu live CD or Ubuntu Rescue Remix (since the data recovery tools are there if the partition is completely unrecoverable), and attempt another fsck with sudo (since your corrupted /usr isn't used when booted from a disc). 
if that fails, I would probably see if it still appears to testdisk.

 I am not sure how you would install just a /usr from an ubuntu CD. if nothing else, many of the programs you installed after OS install put data in /usr, so the system (apt/dpkg) would believe that the app was installed but it;s bins and resources may not be there anymore. I would try to repair the one you have, or backup my personal data in prep for a clean rebuild.

---

### Post by surferX on 2010-12-03
endotherm

I am travelling and have very limited resources (bandwidth and software).
My goal is at least boot the machine so I can assess the damage, which I think is just a failure to mount /usr because it is corrupted. I could live with a ro /usr parition for a week or to if I could boot the machine.

a full cd image of ubuntu is going to take 8 hours to download.

I tried the rescue mode which I believe boots with the options: ro and single which actually still started X and gdm...

If i can somehow tell ubuntu to mount the filesystems read only and give me a command prompt then I would have a chance...

---

### Post by endotherm on 2010-12-03
> **surferX said:**
> endotherm

I am travelling and have very limited resources (bandwidth and software).
My goal is at least boot the machine so I can assess the damage, which I think is just a failure to mount /usr because it is corrupted. I could live with a ro /usr parition for a week or to if I could boot the machine.

a full cd image of ubuntu is going to take 8 hours to download.

I tried the rescue mode which I believe boots with the options: ro and single which actually still started X and gdm...

If i can somehow tell ubuntu to mount the filesystems read only and give me a command prompt then I would have a chance...
then a small livecd like those mentioned above are probably your best bet,. I think the question of running /usr as ro depends entirely on exactly what is corrupt about the drive, so very case by case.
rescue should load without booting x/gdm, so I am not sure what you are experiencing.  I haven;t tried recovery mode on maverick yet, so perhaps they tried to put a gui on it, but I think that would be a mistake.

---

### Post by surferX on 2010-12-03
Thanks for all fantastic help.

[LEFT][Parted Magic]("http://partedmagic.com/")  would not boot, (perhaps a problem with isolinux and my old thinkpad and found some known bugs on the net about the problem, but not sure if was fixed for the version I downloaded)

gparted booted fine! and all I needed was fsck /dev/vg1/usr  and the partition is now clean and the machine boots fine!

I used to use gentoo for many years, when a problem with a partition occurred during the mount process the system give me command prompt. I wonder if ubuntu can be set up in a similar manner?

Thanks again particularly to Herman who saved me from a HUGE hassle!!! :p




[/LEFT]

---

### Post by dcstar on 2010-12-04
> **surferX said:**
> Thanks for all fantastic help.
........
Thanks again particularly to Herman who saved me from a HUGE hassle!!! :p

**Solved** then, is it?

---

