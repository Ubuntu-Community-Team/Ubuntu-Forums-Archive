---
title: "Dual Boot, Sharing Files on different partitions"
date: 2010-06-28
forum: General Help
---

### Post by oni5115 on 2010-06-28
Setting up an old machine for some family members that are not so tech savvy.  It will dual boot Windows XP and Ubuntu 10.04.  The partitioning is as follows:

sda1 12 Gb ntfs WinXP
sda2 ----- ---- Extended
sda3 10 Gb ext4 Ubuntu
sda4 50 Gb ntfs Data 
sda5 02 Gb swap

Note that I did not make "Data" the /home directory.  Last time I tried that using ntfs it wanted me to format it to ext.  I've used the ext drivers in XP before successfully, until the ext3 inode size changed and made it a pain, hence the nfts.

What I'd like to do is point all the windows folders (My Documents, My Photos, etc) to the D drive.  Also, do the same for the Linux equivalents.  That way they can easily find their photos and such in either OS.

What is the best way to do this?  Using symlinks?  
Will I have permission issues with ntfs? 
What is the Public folder for in Ubuntu?

---

### Post by oldfred on 2010-06-29
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

You can directly mount it in everyone's /home or link it into home from another mount location. Mounts in media & home appear again in the side panel so I like to mount somewhere else and link. But I originally just mounted a shared NTFS directly into /home.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

You have to make a mount point:
mkdir /home/fred/shared
Find your UUID:
sudo blkid
Add entry like below to fstab with your UUID:
gksudo gedit /etc/fstab
Remount fstab to make sure there are no errors (just returns to terminal)"
sudo mount -a

# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0

---

### Post by artemyv on 2010-06-29
I could suggest to take a look at the "Storage Device Manager" application in Ubuntu. I have installed it and used to configure what partitions should be mounted at what points, also gives a possibility to specify additional parameters.

So you do not need to work with fstab directly.


About moving "My Documnts" to another location [http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

Using properties you can specify location of most of predefined folders on WinXP (like temp itet files, coocies, ...)

---

### Post by oni5115 on 2010-06-29
Thanks, I ended up using pysdm (the synaptic name of Storage Device Manager) to mount the data drive.  Then was able to quickly create symlinks of the Documents, Videos, etc. folders I made to the home dir using ctrl + shift + drag in Nautilus.   Delete home dir folders, rename links, and POOF.  Working great.

Windows I followed the guide and used the properties menu.  Removed the My Photos and directory.  We'll see how it works.  So far no problems.

---

