---
title: "Trashed filesystem and no grub"
date: 2009-08-30
forum: General Help
---

### Post by Zeroangel on 2009-08-30
I have a dual boot system with several partitions. My windows partition is /dev/sda1 and my mint partition is /dev/sda5
 
Tonight I decided to hook my PC up to my main TV in order to watch movies on it, but right after the grub screen went to boot into linux, I noticed my keyboard wasnt plugged in so I flicked the power switch to the 'off' position before any of the bootup text appeared on the screen.
 
Upon rebooting, X would not start -- warning me that the filesystem was read-only.
 
So I ran "sudo fsck /dev/sda5"
 
Well, it came up with a message saying that the ext4 journal was bad, and asked me to clear it (thus temporarily making it into an ext2 filesystem). I selected yes, then I ran fsck again.
 
This time there were hundreds of errors. Missing inodes, bad symlinks, etc etc. Some of the errors were even illogical looking, like the folder ".." having errors. 
 
I just held the 'y' key on my keyboard hoping it would be over soon but the errors just kept coming. Eventually they stopped and fsck asked me to reboot. So I typed in "sudo shutdown now" and "sudo reboot" but they werent working.
 
I hard rebooted and after posting I was greeted to a black screen
 
"Error 15" was the sum of it.
 
As a result, I booted into my "Linux Mint 7" LiveCD and tried to run fsck, but fsck gave me a message about a bad superblock, or wrong FS type. 
 
I opened gparted to see what was up, and according to gparted, "/dev/sda5" was an "unknown filesystem type"
 
So, from the liveCD, I installed and ran 'sudo testdisk /dev/sda" and it recognized /dev/sda5 as an ext4 partition, so I wrote that configuration to disk -- and testdisk warned me that the configuration wouldnt take effect until the system was rebooted.
 
I rebooted, and nothing happened.
 
What should I do from here?

---

### Post by Zeroangel on 2009-08-30
Argh.
 
I ran testdisk again, and chose to view the files on the ext4 filesystem. Well, quite simply the filesystem looks empty except for the lost+found directory.
 
Am I screwed? Or is there a way to recover from this gracefully?

---

### Post by Zeroangel on 2009-08-30
It appears as if my problem is unrecoverable. I was hoping there would be a backup of the file index or table and a way to restore it, but it doesnt seem to be the case. Regardless, I did the smart thing when creating partitions, and stored a majority of my document types (music, videos, pictures, downloads) in seperate folders on a very big 'shared files' partition (symlinking them to /home/$USER), in case situations like this happened. However, i still lost a lot of stuff and its gonna take me hours to re-install and recustomize.
 
Oh well, things like these happen every once in awhile.

---

