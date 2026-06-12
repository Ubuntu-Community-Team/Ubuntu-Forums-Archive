---
title: "deleted files on 2nd partition"
date: 2011-03-15
forum: General Help
---

### Post by xfearxnxloathing on 2011-03-15
for some reason, when i delete files from my 2nd partition (only used for storage) after logging in as root, it doesnt free up space. i've delete over 60gigs of stuff and no space has been freed, please help!!

---

### Post by oldfred on 2011-03-15
Did you emtpy trash?

Logging in as root probably put them files into a root trash.

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Trash
Here is where these files normally reside.

    * ~/.local/share/Trash User's Trash (hardy and later)
    * ~/.Trash User's Trash (pre-hardy)
    * /root/.local/share/Trash System Trash (hardy and later)
    * /root/.Trash System Trash (pre-hardy):
    * /.local/share/.Trash-1000 NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc

rm -rf ~/.local/share/Trash/*

If you get permission problems try to slip a sudo in front of the commands, but be sure that the path is correct.

Sometimes it is necessary to change the ownership of the trash files:
sudo chown -R yourusername /home/yourusername/.local/share/Trash

---

### Post by xfearxnxloathing on 2011-03-15
> **oldfred said:**
> Did you emtpy trash?

Logging in as root probably put them files into a root trash.

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Trash
Here is where these files normally reside.

    * ~/.local/share/Trash User's Trash (hardy and later)
    * ~/.Trash User's Trash (pre-hardy)
    * /root/.local/share/Trash System Trash (hardy and later)
    * /root/.Trash System Trash (pre-hardy):
    * /.local/share/.Trash-1000 NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc

rm -rf ~/.local/share/Trash/*

If you get permission problems try to slip a sudo in front of the commands, but be sure that the path is correct.

Sometimes it is necessary to change the ownership of the trash files:
sudo chown -R yourusername /home/yourusername/.local/share/Trash

Totally checked for those already but I found when I went to that particular partition (not where root was installed or Ubuntu for that matter) that hitting "ctrl+h" made two trash folders appear, everything I deleted was still sitting in one of them.  The two folders were, ".Trash-0" and ".Trash-1000", the deleted files were in ".Trash-0".  Should I delete ".Trash-1000"?

---

### Post by oldfred on 2011-03-16
I think trash 0 is root & and trash 1000 is you as the first user.

Root has a uid of 0 and the first user is 1000 in Ubuntu.

---

