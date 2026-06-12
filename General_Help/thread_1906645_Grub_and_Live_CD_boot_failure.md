---
title: "Grub and Live CD boot failure"
date: 2012-01-09
forum: General Help
---

### Post by micascisto on 2012-01-09
Hi everyone,

I've been using ubuntu for 3 years and encountered many problems and I always solved them quite easily, but not this time!

I have a Asus Eee PC 1000HE with Ubuntu 10.04 and Windows XP SP3.
My 160GB HD has these 4 partitions:
-Windows XP SP3, ntfs, 30GB
-Personal data partition, ntfs, about 90GB
-Fast boot partition, about 40MB
-Ubuntu 10.04 on ext4 + swap in 2 logical partions, 28GB+2GB respectively.

I used ubuntu for 3 years without big problems, I also formatted it and reistalled 1 time for upgrading from 9.04 to 10.04, so I'm not new and tried a lot of solution for my problem.

Here is the problem:
-if I try to boot from grub (both normal and recovery mode options) it results in a blank screen. I tried to solve editing grub by pressing ctrl+e and following instructions found on forums but  I received an error message stating that it failed to mount /dev, /sys/, /proc, and that the target filesystem doesn't have /sbin/init. I tried a lot of solutions with grub, but no-one worked.
-if I try to boot the 10.04 Live CD, it stops loading quite soon and by pressing F2 it shows this message:

stdin: error 0
unable to open '/dev/sda'

Other infos: 
-I can boot Windows XP, the Linux partition is fine since I was able to open it with "ext2read" and save my personal files in the home folder.
-So I can access every file and folder on Linux partition, if you need a specific file for helping me just ask for it!
-the Live CD is ok, it is the CD I used for installing Ubuntu 10.04 just a few days ago on another PC, please don't ask me to check MD5 because the CD it's fine!)
-I'm italian, so excuse me for the language errors!
-Someone else had the same problem on another forum, it seems to be a problem with the linux partition's filesystem but there is no working solution since I'm not able to load the live cd and repair the filesystem.

is there anyone who can help me?

a solution may be to format the partition from Windows XP, but I'm worried by the chance that I won't be able to run the Live CD installer to install again Ubuntu and grub for the same problem that happens now.

---

### Post by Basher101 on 2012-01-09
if the 10.04 CD is not working, try a newer CD to fix things.

this is all that comes to my mind...

regards and good luck

---

### Post by micascisto on 2012-01-09
It worked! Thank you so much!

Here is the real problem:
-fstab has been edited by Dropbox (don't ask me why or how)! When I opened fsatb, I saw a comment by Dropbox and the two lines of the ext4 and swap partition commented. A new line for the ext4 partition has been created, but it was different from the original one. Unfortunately, I didn't make a copy of it to be posted here, because I deleted it and just copied the working backup copy. It was like this:

# Commented out by Dropbox
# UUID=47b7c726-0d5c-4c52-958b-0183c873b345 /        ext4    errors=remount-ro 0       1
# UUID=dcfb5991-5d9d-4990-9326-6e01dc2ad03d none  swap    sw              0       0
UUID=47b7c726-0d5c-4c52-958b-0183c873b345 /         ext4    errors=remount-ro,user_xattr 0       1

And here is the (simple) solution:
-Run the Ubuntu 11.10 Live CD normally
-Edit fstab by uncommenting the two lines and deleting the added one. I had a working backup, so I just deleted the wrong fstab and made a copy of the right one.

Now everything works normally. Thank you!

---

