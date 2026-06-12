---
title: "Windows XP and the fourth extended file system"
date: 2009-08-16
forum: General Help
---

### Post by Cadeyrn on 2009-08-16
I'm running x64 Jaunty on an ext4 system, and proud of it. However, I am faced with a dilemma--the two main programs for viewing ext on Windows, EXT2IFS and EXT2FSD each have a drawback that doesn't work for me.

EXT2IFS is known for only being able to read ext's with inodes of 128 bytes, and I don't want to reformat my Linux partition. But EXT2IFS version 1.11 said somewhere in the website or the installer that ext4 is now supported.

EXT2FSD actually works with more than just the extreme minority of ext users by reading inodes of 256 bytes, but it still hasn't reached ext4 support. Not only does it read my ext4 drive as ext3, but when I tried mounting it, the folders were there, except the etc folder said access denied when I tried to open it, and all the other folders were empty. So unless I'm in Windows and I want to show someone the Ubuntu set of main folders without rebooting, it's not very useful.

I'm wondering, since EXT2FSD is so close to properly mounting an ext4 drive even if it does think that drive is ext3, and EXT2IFS just needs to read inodes of 256 bytes, maybe someone could mod one of the programs to read ext4? I don't need write support; only read. I'm a fast learner, so if there's someone who'd rather teach me how to mod these programs instead of do it themself I'm open to it.

---

### Post by HermanAB on 2009-08-16
Howdy,

Dual booting is so 20th Century!  Get with it and run Windows in Virtualbox or VMware, then you can connect to the Linux file system through the network using SSH, FTP, Samba or NFS.  Then it doesn't matter what file system Linux is using.

---

### Post by Cadeyrn on 2009-08-17
Oh, how I'd love to do that... if you want details on why I cant, look here:

[http://ubuntuforums.org/showthread.php?t=1218499](http://ubuntuforums.org/showthread.php?t=1218499)

---

