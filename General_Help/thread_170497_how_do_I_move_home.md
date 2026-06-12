---
title: "how do I move home?"
date: 2006-05-04
forum: General Help
---

### Post by the_tiger on 2006-05-04
I have formated a partition as home so that i may isolate my files in the need of a fresh install. How do I now move my home from one to the other?

---

### Post by tburns on 2006-05-04
usermod -d 

a couple of links and also use: man usermod

[http://www.ss64.com/bash/usermod.html](http://www.ss64.com/bash/usermod.html)
[http://linux.about.com/od/commands/l/blcmdl8_usermod.htm](http://linux.about.com/od/commands/l/blcmdl8_usermod.htm)

---

### Post by yabbadabbadont on 2006-05-04
For my example, let us assume that you have mounted your newly created and formatted home partition onto /mnt.  Then you would do something like this:

Make a backup of your current home directory somewhere using whatever method with which you feel comfortable.  (i.e. tar, cpio, ...)

sudo cp -a /home /mnt
sudo gedit /etc/fstab    (add an entry in there for /home that uses the new partition)

Reboot the system.  If everything works correctly, you may want to remove the old files to save disk space.  To do this, you will need to boot a livecd.  Then mount your root partition.  Now simply rm -r the contents of the home directory that is on the mounted root partition.  (e.g something like rm -r /mnt/home/*)  Umount the partition and reboot.

If you need more detail, post the current contents of your /etc/fstab file, the output of "sudo fdisk -l", tell us which partition is your new home, and which filesystem you used to format it.

---

### Post by jerrykenny on 2006-05-04
Hi Tiger, that's not too clear, it sounds as if you've formatted a "spare" partition, is that right ?

if so you can try the following

sudo mkdir /mnt/spare
sudo mount /dev/hd??  /mnt/spare
sudo cp /home/tiger /spare/tiger2


If you then go for a fresh install, you can maybe mount that partition at the installation stage, but not sure if debian allows you to specify an existing /home/directory for the new user, if not then make a new user, say leopard, log in as leopard go to system admin, users & groups, make a new user "tiger" and specify his home directory ie "/home/tiger2"

---

### Post by jerrykenny on 2006-05-04
OK yabba, you beat me on the draw there . . .

---

