---
title: "Worth the effort to reformat?"
date: 2011-07-03
forum: General Help
---

### Post by ubunwhat on 2011-07-03
Silly question, perhaps.  I am currently putting a fresh install of Ubuntu on another machine and it has me wondering about the one I am currently using.  I did this install when I was new to Linux and rather stupid about the whole thing.  It does, however, work.  Which is saying quite a bit considering the hours spent getting the wireless to work after upgrading to 11.04.  So what I am wondering now is whether it would be worth the time and effort to back up all of my data from this machine, reformat this disk, and try again.  I actually think I am sitting on an NTFS disk right now.  I'm wondering if the performance and speed improving of switching to ext4 would merit the hassle of backing up and re-installing everything.  Or would I be able to create a disk image, reformat, and then just lay the image back down?

---

### Post by Bucky Ball on 2011-07-03
Ubuntu will not install on NTFS so that is not possible, unless you have a Wubi install *inside* Windows which is a Wubi install, not a regular install on HDD.

If it is a Wubi install, you will get a speed improvement (and a whole lot more) from a regular hard drive install.

If you have the time, and it shouldn't take much, I would go to the bother of having a good look at Gparted at what you currently have, make a plan, and go for it! I stick to the LTS releases myself but have a couple of 15Gb partitions spare for installing other things. You might want something like:

/ = 15-20Gb (is plenty)
/home = big as you like
/swap = size of your RAM (the debate continues, though; some say twice the size of RAM is you hibernate)

This way, if you upgrade or want to clean install in future your personal data in /home is safe and you can just kill / by re-installing over it. Just for ideas, I have:

/Windows7 = 40Gb, NTFS
/10.10 = 15Gb, EXT4
/10.04 minimal install = 15Gb, EXT4
/OS2 partition empty = 15Gb, EXT4
/home = 145Gb, EXT4
/misc = 40Gb, NTFS: to share data with Win7
/swap = 4Gb

Have fun. Just remember: Windows *cannot* read/write EXT* partitions natively. Ubuntu/Linux *can* read/write NTFS partitions. ;)

After some thought, you may decide you only need to adjust the sizes of your partitions rather than re-install. To do this, boot from the LiveCD and use Gparted. Unmount the partitions you want to shrink/expand. Good luck.

---

### Post by bcbc on 2011-07-05
See [HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354")

You'll probably see an increased performance moving off Wubi, but not a huge difference and not in all areas - I notice it more in booting up; otherwise it depends on what you are doing. See [here]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1")

But a regular install is much safer in terms of reliability. Wubi stores everything on one file (so all eggs in one basket).

---

