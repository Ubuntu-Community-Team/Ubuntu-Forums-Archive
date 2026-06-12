---
title: "Emptying Trash hangs, manual delete too... :("
date: 2009-08-01
forum: General Help
---

### Post by brettw.10 on 2009-08-01
Hi guys,

I am running Jaunty kernel 2.6.28-14 on my Intel Celeron 2.6GHz based PC at home and am having problems with the Trash system.  Every time I try and empty the trash, my system hangs.

Looking in my ~/.local/share/Trash directory, I find a bunch of files and directories in the expunged subdir, and nothing in the files dir.  When I try and run an "rm -rf" in the expunged directory the system hangs as well.

I tried moving the files out of expunged to another dir and deleting them from there, but this caused the system to hang too.

Anyone got any suggestions that could help me out?  The problem is that my root file system is now at 99% utilisation and I cannot clean it up due to this trash issue.

Regards,
Brett.:confused:

---

### Post by 4Orbs on 2009-08-01
I am guessing that you installed Ubuntu using the ext4 file system. I re-installed mine back onto ext3 because of the trash problem and other quirks with ext4. Some people have no problems with ext4, but those of us who have experienced troubles cannot seem to find a fix. Eventually, hopefully ext4 will work well for everyone. If you are not using ext4, then I will humbly exit this thread.

You can get some extra empty space by removing the cached packages for programs you have already installed by entering in a terminal: sudo apt-get clean

---

### Post by brettw.10 on 2009-08-01
True, I have an ext4 root filesystem.  I really don't want to have to reinstall to switch to an ext3, but I guess that I have no choice.  :(

---

### Post by stpaddles on 2009-08-20
I am experiencing the exact scenario described on my EEE900.  Is there any danger in manually clearing the /expunged directory?

nicholas

---

