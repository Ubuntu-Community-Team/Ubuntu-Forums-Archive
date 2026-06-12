---
title: "maverick boot / mount problem after restore from tar archive"
date: 2010-12-29
forum: General Help
---

### Post by thode on 2010-12-29
This method used to work with Karmic and before.

I think it's a very popular way of creating backups. I use the following command to create the backup:
> sudo tar -cvpzf backup.tar.gz --exclude=/backup.tar.gz --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/lost+found --exclude=/proc /

Something goes wrong, I format the ext4-partition and then boot from the Ubuntu live-CD. Run the following command in terminal:
> sudo tar -xvpzf /media/xxx/backup.tar.gz -c /media/yyy

yyy is the uuid from the formatted ext4-partition.
Then I have to change that uuid in /etc/fstab and /boot/grub/grub.conf.

Normally this should work but since Maverick (and maybe Lynx) I get the following error when I've selected the Ubuntu OS from the grub menu:
> 
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
init: error while reading from descriptor: bad file descriptor
init: hwclock main process (365) terminated with status 127
init: plymouth main process (364) terminated with status 127
init: ureadahead main process (366) terminated with status 3
/bin/sh: Can't open /proc/self/fd/8
init: mount all main processes (367) terminated with status 127


---

### Post by thode on 2011-01-02
Any ideas?
Anyone who uses the same method and doesn't have a problem? Or has a similar working method?

---

