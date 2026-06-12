---
title: "HD Space Mysteriously Dissapears"
date: 2010-02-08
forum: General Help
---

### Post by Heeshung on 2010-02-08
About a week ago I installed 9.10 onto my laptop, which is dual-booting with Windows 7.  I shrinked the Windows 7 partition from 500GB to 490GB.  Out of the 10GB, 2GB went to swap.

I had set my Windows partition to be automatically mounted every single time Ubuntu started up, so that I didn't need to manually mount it.  Ubuntu worked wonderfully up until now.  About two days ago, I checked the free space in the Ubuntu partition out of curiosity and it showed about 4GB of free space.  Today, however, I got an error message warning me I only had 40MB of space left.  About 10 minutes and a reboot later, it was 10MB.  Now it's at 0.

I did absolutely nothing, except write a couple text files, download a couple images, and compile a couple .out files.  I did access files stored in the Windows partition.  However, I just cannot see where my space is going.  I can't even run Kdirstat because of the lack of free space.  It seems like it is literally disappearing.

---

### Post by juancarlospaco on 2010-02-08
**sudo apt-get clean**

---

### Post by oldfred on 2010-02-08
Also these:
HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates depend

OWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by Heeshung on 2010-02-08
Thanks for the replies; I haven't tried any of those yet, because the problem just got weirder.

When the free space lowered, I was using Ubuntu on battery for the first time.  I decided to plug the laptop back in to do the 'sudo apt-get clean' but when I checked the free space, it was back at 3.5GB.

I bet if I disconnect the power and let it run on battery again, it'll lower.  What's going on?

---

### Post by darolu on 2010-02-08
Out of curiosity, what do you get with:
```
sudo fdisk -l
```

---

### Post by Heeshung on 2010-02-08
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e9ea7b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       59586   478515625    7  HPFS/NTFS
/dev/sda3           59587       60801     9759487+   5  Extended
/dev/sda5           59587       59828     1943833+  82  Linux swap / Solaris
/dev/sda6           59829       60801     7815591   83  Linux
```
During one of the battery-powered reboots the login screen turned into a white one and the following popped up at the top right:

[B]"Install Problem!" The Configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.

[/B]I plugged the computer back in and then rebooted and the message did not appear.

---

### Post by darolu on 2010-02-08
Weird how GNOME Power Manager affects your HD space but it seems to be the problem, this threads may help you:
[http://ubuntuforums.org/showthread.php?t=1355880](http://ubuntuforums.org/showthread.php?t=1355880)
[http://ubuntuforums.org/showthread.php?t=785012](http://ubuntuforums.org/showthread.php?t=785012)

---

