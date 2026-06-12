---
title: "Creating /boot Partition After Installation"
date: 2010-12-18
forum: General Help
---

### Post by th5th on 2010-12-18
Hey all,

I have happily been using Ubuntu and only Ubuntu for the last 3 or 4 months. I have a bit of experience with Linux before that so I know that if I try and do this without asking first, something will go horribly wrong.

Basically I want to create a /boot partition so I can install other Linux distros on my system without having GRUBs fighting each other etc. etc.

I feel like something along the lines of:

1. Boot Ubuntu or GParted live USB.
2. Create new partition for /boot.
3. Mount / partition and new /boot partition.
4. Copy contents of /boot folder onto new partition
5. Mess with fstab / GRUB to make it work.

As you may have guessed step 5 is what I am unsure of. Any tips would be appreciated!

Edit: It's a 10.04 Lucid install if that makes a difference.

---

### Post by oldfred on 2010-12-18
Even with additional installs you do not want a separate /boot or you have to create a separate /boot for each and every install. 

You can do a separate /boot just the way you list. I did it with old grub but then changed that I really only wanted a grub only partition and moved /boot back(all in the same day, so I only have had a /boot for a few hours). You have to reinstall grub & edit fstab with the /boot partition.

Only one bootloader can be in the MBR and it will control your boot. I like and use grub2 with Ubuntu. But you have to decide which bootloader you want in charge. Ubuntu's grub2 osprober is very good at finding other installs, so it makes it easy to boot other systems.

Herman on advantages/disadvantges of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

