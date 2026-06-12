---
title: "Grub rescue problem"
date: 2011-02-08
forum: General Help
---

### Post by Szamko on 2011-02-08
Hi all,

I seem to have made my hardware unusable today and I wonder if anybody here can help out. 

To begin with, I esablished a dual boot with Windows 7 and Ubuntu on separate partitions. Then, as I realised that Windows 7 was rubbish and Ubuntu annoyed me by losing wireless connectivity after an update, I decided to go back to Windows XP for a while. So I did what I probably shouldn't have done, and formatted the partition (or so I thought) with Ubuntu on, using Windows.

Now, on booting up the system, all I can get is the Grub Rescue prompt and nothing in the Bios menus seems to be of any assistance.

I've tried booting XP from a CD, but a blue screen error always occurs at the same point in the installation. I wonder if I should make a CD/external drive with Ubuntu on, reinstall it, and go from there?

Any help would be much appreciated.

---

### Post by lindsay7 on 2011-02-08
your mbr still has the grub info on it even though you deleted the ubuntu installation of its OS.  You need to redo your windows mbr. you need to run fixmbr with windows repair options.  You can find info on this on the internet.  You will need the windows install disk to do this.

---

### Post by gordintoronto on 2011-02-08
If you get a blue screen while trying to install Windows, your computer probably has hardware problems.

---

