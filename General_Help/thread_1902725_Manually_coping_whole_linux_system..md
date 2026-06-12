---
title: "Manually coping whole linux system."
date: 2011-12-31
forum: General Help
---

### Post by nivwusquorum on 2011-12-31
Hi,

I am moving from one disk to another. I tried to use Norton Ghost to back-up current partitions. 

Unfortunately even the newset one fails when copying my linux partition.

So now I am doing a manual copy. (Just copying all the files, while running livecd, so that copied linux is off).
Now the there are two problems:
1. when copying system complaint about how it's impossible to copy special files. I thought these are only created on start-up, but clearly I was wrong. How would this affect possibility of manual copy?
2. after copying partitions over to new disk their UUIDs will change. How do I restore grub and fstab easily. Is there anything else I have to restore to succesfully boot copied system?

Thank you,
Szymon

---

### Post by vpharry on 2011-12-31
> **nivwusquorum said:**
> Hi,

I am moving from one disk to another. I tried to use Norton Ghost to back-up current partitions. 

Unfortunately even the newset one fails when copying my linux partition.

So now I am doing a manual copy. (Just copying all the files, while running livecd, so that copied linux is off).
Now the there are two problems:
1. when copying system complaint about how it's impossible to copy special files. I thought these are only created on start-up, but clearly I was wrong. How would this affect possibility of manual copy?
2. after copying partitions over to new disk their UUIDs will change. How do I restore grub and fstab easily. Is there anything else I have to restore to succesfully boot copied system?

Thank you,
Szymon
You can use remastersys to create a separate bootable backup... then u just reinstall it... everything will be back up.... :D Hope that helps...

---

### Post by galvatron408 on 2012-01-01
you need to use dd to do the disk copy; here's a good article on it.

[http://www.cyberciti.biz/faq/linux-unix-copy-clone-hard-disk/](http://www.cyberciti.biz/faq/linux-unix-copy-clone-hard-disk/)

---

### Post by hal8000 on 2012-01-01
> **nivwusquorum said:**
> Hi,

I am moving from one disk to another. I tried to use Norton Ghost to back-up current partitions. 

Unfortunately even the newset one fails when copying my linux partition.

So now I am doing a manual copy. (Just copying all the files, while running livecd, so that copied linux is off).
Now the there are two problems:
1. when copying system complaint about how it's impossible to copy special files. I thought these are only created on start-up, but clearly I was wrong. How would this affect possibility of manual copy?
2. after copying partitions over to new disk their UUIDs will change. How do I restore grub and fstab easily. Is there anything else I have to restore to succesfully boot copied system?

Thank you,
Szymon

Use DD to copy the partition as already sugested you dont need Norton Ghost. After moving the partition the UUID will change, and also the copied /etc/fstab will point to the old UUID values.

After copying or moving the partition, boot with the Ubuntu CD in live mode, then list the UUID of your new partitions:

sudo ls -l /dev/disk/by-uuid/

This will show the UUID of all partitions. You then have to mount your new / partition and edit fstab so that /, /home and /tmp are ponting to the correct partitions.
You then need to re-install grub2:

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by rsvancara on 2012-01-01
You can also use blkid to obtain the UUID of the partitions.  If you are using the recovery CD, the symbolic links may not exist.

blkid /dev/sda1

-- Randall
[Know your Linux?]("http://www.knowyourlinux.com/")

---

### Post by dcstar on 2012-01-02
> **nivwusquorum said:**
> Hi,

I am moving from one disk to another. I tried to use Norton Ghost to back-up current partitions. 

Unfortunately even the newset one fails when copying my linux partition.

So now I am doing a manual copy. (Just copying all the files, while running livecd, so that copied linux is off).
........
[LIST=1]
[*]Boot Live CD.
[*]Start gparted.
[*]Use gparted "Copy" and "Paste" function to copy existing Linux & Swap partitions to new drive.
[*]Change UUID of copied partition on the new drive (search forum for detailed instructions).
[*]Boot existing system and then do "sudo dpkg-reconfigure grub-pc" and install bootloader on new disk.
[*]Shutdown, remove old drive and boot up.
[/LIST]

---

