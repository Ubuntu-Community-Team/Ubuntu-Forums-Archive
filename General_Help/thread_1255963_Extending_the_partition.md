---
title: "Extending the partition?"
date: 2009-09-02
forum: General Help
---

### Post by avolkov on 2009-09-02
Hello all. I'm brand new to ubuntu, in fact, this is my first post on the forum. 

The other day I had vista on my pc, and I decided to start a new life with linux. Well, not a new life, more of a parallel, since my original plan called for simply dual booting vista and ubuntu. Well... i accidentally deleted vista... oops. Now I have a small, 50 gb partition for ubuntu, which I now want to keep as my main OS, and a lot of space (like 400 gigs) on an empty ntfs partition that is positioned "before" my ubuntu partition. there is also a swap space at the end of the harddrive, but that's really irrelevant. 

What I want to do is add like 300 more gigs to the ubuntu partition from my ntfs partition, without losing ubuntu, and still be able to also install vista on the remaining 50 gb of ntfs left over from before... I know its specific, but I was hoping someone could break the process of doing this down, if its even possible, especially the "without losing ubuntu" part. 

Thanks in advance,
AV

---

### Post by P4man on 2009-09-02
read this how-to:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by vanadium on 2009-09-02
I would not enlarge the existing installation. 1) there is no need 2) it will be a slow process because you will need to move the Ubuntu partition 3) I am not sure if partition UUIDS are preserved, which would cause a need to change UUID's of the partition back, or update them in various configuration files.

* Just leave your existing Ubuntu installation untouched
* Reformat the ntfs partition to a linux file system (ext3). You can use gparted for this. Install it in your normal Ubuntu system (Use Synaptic package manage or the command "sudo apt-get install gparted") and run it from there ("gksudo gparted"). That way, you won't be able to accidently reformat your root partition.
* Mount the reformatted ntfs partition, for example under "/mnt/data". You should have this done automatically by including a line for the partition in /etc/fstab (ask further help for this if needed).
* Create a link from within your home directory to directories on that partition (and eventually do the same for other users): you now have seamless and instant access to that storage.

---

### Post by avolkov on 2009-09-02
I downloaded gparted. Can you explain the last 2 steps you wrote vanadium? From "Mount the reformatted ntfs partition" 

Also, the ntfs partition currently has the boot flag on it, should I add the boot flag to my "main" linux install partition?

---

### Post by avolkov on 2009-09-02
slightly urgent, so bump

---

### Post by stuart.reinke on 2009-09-02
If you intend to put Vista back on your machine, I will be simpler to back up any important data and then reinstall Vista using the entire disk. Then reinstall Ubuntu. 

The Ubuntu installer will install the grub boot loader which will include an option for Windows and Ubuntu. However Windows bootloader will not recoginze Ubuntu if it is already on the drive.(it wipes out Grub)

It can be done with Ubuntu on first but you will have to manually install Grub, and configure the menu.lst file after the windows install.

---

### Post by vanadium on 2009-09-03
To mount the new partition automatically during startup, you need to add a line to /etc/fstab.

* find the UUID of your new partition. It will be listed on one of the lines in the output of "sudo blkid"
* create a mount point (=empty directory) for your new partition: "sudo mkdir /mnt/data"
* for safety, make a backup copy of your "/etc/fstab" first: "sudo cp /etc/fstab /etc/fstab.backup"
* edit your /etc/fstab with root permissions: "gksudo gedit /etc/fstab". Add a new line of the following form

UUID="....." /mnt/data/ ext3 defaults 0 2

where you should fill out the correct UUID as you found in the output of "sudo blkid" (tip: copy/paste from terminal into gedit to avoid having to type this long UUID). The second entry is the mount point you created.
* Save your /etc/fstab and exit gedit
* Mount the new partition by re-executing /etc/fstab: "sudo mount-a". There should not by any error message. Otherwise, there is something wrong with your edit.

Your partition is now available in /mnt/data, but you cannot yet write to it as a regular user. If you are the only user, you can as well assign the whole partition to yourself by changing the owner of the mount point. You can use the following command literally: "sudo chown $USER:$USER /mnt/data". For systems with multiple users, I'd rather create subdirectories on the partition as root, and assign these to different users.

To make access to your data easy, create a link in your own home directory. Then you never need to navigate outside of your home to find the data: "ln -s /mnt/data ~/data". This will create a symlink "data" (you can name it like you want) in your home directory that acts and behaves as a true directory.

---

