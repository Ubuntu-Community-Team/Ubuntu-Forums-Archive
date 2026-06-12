---
title: "Need to back up Vista for Ubuntu installation, but not sure how"
date: 2011-01-15
forum: General Help
---

### Post by sKRiBEL on 2011-01-15
i need to backup my Vista Home Premium entirely, including the OS itself, just in case i screw my whole hard drive up during this process, and i need to reinstall vista and my data. I have a 1tb external Hard Drive with a ~700gb FAT32 empty partition on it (i can re-format this if necessary), I need to be able to backup my operating system entirely to this. 

Example of why i wish to back this up: Let's say im installing ubuntu, and i accidentally install it over my vista partition, now i have no vista in my machine whatsoever, i want to be able to use this backup i have created to reinstall vista onto the hard drive.

Does anyone know of any software or anything that would allow me to do this, preferably free. Help would be much appreciated ^^ :]

more info on why im doing this: [http://ubuntuforums.org/showthread.php?t=1667357](http://ubuntuforums.org/showthread.php?t=1667357)

---

### Post by coffeecat on 2011-01-15
You need to make a disk or partition image, but don't use a FAT32 filesystem to back up to. The Vista disk image will be one huge file, many gigabytes in size, and FAT32 has a 4GB filesize limit. Reformat it to NTFS. You can do this in Vista, or use Gparted in Ubuntu.

For making the partition image, I can recommend Macrium Reflect Free Edition:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It's proprietary software, but free. I prefer it to the paid-for Acronis True Image. I've used Macrium to backup (and more importantly, restore) Windows XP, Vista and Windows 7. You make a bootable rescue CD from within Macrium. The CD is Linux-based.

Some people recommend clonezilla for what you want. Macrium is much more user-friendly.

One thing to be aware of. Macrium will only restore an image to a partition the same size or greater than the original. So if your Vista occupies the whole hard drive now, it can only be restored to the same size as originally, after which you can use the Vista Disk Management tool to make it smaller if you want.

---

### Post by sKRiBEL on 2011-01-15
ok thank you, i was actually trying macrium, as for re-formatting and stuff i usually just use gparted so thats what I'll do thatnks for the insight ^^ :]

---

