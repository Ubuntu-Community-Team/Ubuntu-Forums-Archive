---
title: "Grub woes, 9.10, dual boot with Vista"
date: 2010-07-18
forum: General Help
---

### Post by SavageFreedom on 2010-07-18
First, I apologize if I've overlooked an identical issue in the forum, but generally there is a difference in the problem that causes the offered solutions to be invalid.

Here's the deal:

I have 3 HDDs, 1 NTFS running Vista, 1 with a small partition for Ubuntu and the remainder of the drive being either NTFS or FAT32, and one backup drive with no OS. As for the Ubuntu partition, I installed Ubuntu Studio (9.10 I think, maybe it's 9.4?) after the new GRUB had caused me problems before that I was at that time unable to fix. Just re-parted it, clean install, worked great for a few days maybe.

Suddenly one day GRUB decided the status-quo was unacceptable and stopped recognizing the proper device mapping, nothing would boot. I was able to fix it by doing

```
sudo grub-mkdevicemap
```
```
sudo update-grub
```

After some time though, it screwed up again. When I checked my device.map file a moment ago, it looked like this roughly:

```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
```

I ran grub-mkdevicemap and checked it again, now it only has the first entry (hd0) and nothing else.

When I run update-grub, here is the output:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-9-rt
Found initrd image: /boot/initrd.img-2.6.31-9-rt
Found memtest86+ image: /boot/memtest86+.bin
[   491.628771] end_request: I/O error, dev sdb, sector 2048
[   491.628824] Buffer I/O error on device sdb1, logical block 0
[   491.628875] Buffer I/O error on device sdb1, logical block 1
[   491.628924] Buffer I/O error on device sdb1, logical block 2
[   491.628874] Buffer I/O error on device sdb1, logical block 3
[   491.629029] Buffer I/O error on device sdb1, logical block 4
[   491.629079] Buffer I/O error on device sdb1, logical block 5
[   491.629128] Buffer I/O error on device sdb1, logical block 6
[   491.629198] Buffer I/O error on device sdb1, logical block 7
[   491.629279] end_request: I/O error, dev sdb, sector 2048
[   491.629348] Buffer I/O error on device sdb1, logical block 0
[   491.641955] end_request: I/O error, dev sdc, sector 2048
[   491.642013] Buffer I/O error on device sdc1, logical block 0
[   491.642111] end_request: I/O error, dev sdc, sector 2048
done
```

Hence why it isn't adding sdb and sdc to the device.map I suppose. But why? Both of these drives function perfectly well. I use one as a backup and it doesn't even have an OS, and the other (with the Ubuntu partition) serves as my media (music/photos/video) drive and is accessed every single day without problem.

When I actually try to boot sda, it gives me the splash, but behind it is this:

```
[    68.397453] end_request: I/O error, dev sda, sector 378239
Zion login: [  128.399250] end_request: I/O error, dev sda, sector 481599
init: rsyslog main process (1428) killed by ABRT signal
init: rsyslog main process ended, respawning
```

Followed by dozens of lines of init errors, caused by either ABRT, PIPE etc, unhandled error codes on sda (with the result of hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK... repeating infinitely until I reboot.

Surely all three of my drives are not failing, as they are all newer drives and I can do a clean install and not have any problems for a few days.

I honestly never had these problems with the old GRUB, and wish I could just edit menu.lst ... I never saw an init error in years prior to this.

---

### Post by dino99 on 2010-07-18
grub2 dont work correctly if menu.lst still there, so remove it, then :

sudo grub-mkconfig
sudo update-grub

grub-pc (ie grub2) need to be installed on the ubuntu hdd

better to set ahci mode into bios and dont use that oldish fat32, ntfs work smootly in every case ( with ntfsprogs on linux side, and fs-driver on windoz side [http://www.fs-driver.org/](http://www.fs-driver.org/))

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by SavageFreedom on 2010-07-18
From what I understand this has always been GRUB2 from the get go, there is no menu.lst. However, I was screwing around, trying to get it to find the proper drives again, and it randomly decided to properly update (or so I thought) and found the other 2 drives without errors. When I tried to boot into either Ubuntu or Vista though, Ubuntu would take me to a terminal, I'd run startx and it would hang as soon as the background appeared, and if I try to boot windows it says "invalid signature" and will not boot. Of course, booting directly into the Windows hard drive has it working perfectly with no problems, so clearly this is some kind of GRUB problem. It's getting old. I don't think I'll ever dual-boot again.

---

### Post by dino99 on 2010-07-18
boot on a live cd or usb stick and check each ubuntu partition:

fsck -n /dev/sdxx (where x is your partiton)

and to repair:

fsck -y /dev/sdxx

---

