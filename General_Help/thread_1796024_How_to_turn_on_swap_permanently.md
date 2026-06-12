---
title: "How to turn on swap permanently"
date: 2011-07-03
forum: General Help
---

### Post by Archy1987 on 2011-07-03
Hi! I created the swap partition, but the problem is, that i have to turn on swaf every time when i turn on my computer. How to turn swap on permanently?

---

### Post by createdcreature on 2011-07-03
Upgrade to Natty or Lucid. There was a long-running bug in Ubuntu concerning swap that was fixed in 10.04 (Lucid Lynx).

---

### Post by Archy1987 on 2011-07-03
> **Robert Moyse said:**
> Upgrade to Natty or Lucid. There was a long-running bug in Ubuntu concerning swap that was fixed in 10.04 (Lucid Lynx).
i tried to upgrade to 11.04, but i had one problem - my wireless pci card was totally refused to work. i was unable to connect to the internet. I don't have this problem with my 9.10 ubuntu. Any other solution?

---

### Post by gandaran on 2011-07-03
> **Archy1987 said:**
> Hi! I created the swap partition, but the problem is, that i have to turn on swaf every time when i turn on my computer. How to turn swap on permanently?
was the swap partition created after or before installation?
check /etc/fstab for the swap partition, post the contents.

---

### Post by Rubi1200 on 2011-07-03
Can you post the output of this command please?

```
cat /etc/fstab
```

---

### Post by Archy1987 on 2011-07-03
I created this swap partition after installation. Original swap partition was deleted, because i moved my ubuntu installation from one hdd to another using clonezilla

archy@archy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fb70ff07-6e27-47a3-9edc-2dedee03f514 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5e664a34-f425-4f79-b268-8a21230786c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
archy@archy-desktop:~$

---

### Post by gandaran on 2011-07-03
> **Archy1987 said:**
> I created this swap partition after installation. Original swap partition was deleted, because i moved my ubuntu installation from one hdd to another using clonezilla

archy@archy-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fb70ff07-6e27-47a3-9edc-2dedee03f514 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5e664a34-f425-4f79-b268-8a21230786c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
archy@archy-desktop:~$
according to fstab swap was on sda5 when you installed ubuntu but now you have swap on sda2 so it's just a simple case or fstab  correction, change sda5 to sda2 and the UUID number
to find out the new UUID type in terminal
```
sudo blkid
```

---

### Post by Archy1987 on 2011-07-03
> **gandaran said:**
> according to fstab swap was on sda5 when you installed ubuntu but now you have swap on sda2 so it's just a simple case or fstab  correction, change sda5 to sda2 and the UUID number
to find out the new UUID type in terminal
```
sudo blkid
```
archy@archy-desktop:~$ sudo blkid
[sudo] password for archy: 
/dev/sda1: UUID="fb70ff07-6e27-47a3-9edc-2dedee03f514" TYPE="ext4" 
/dev/sda2: LABEL="swap" UUID="1a85f554-f315-4fbc-a3c6-1beb22f7ae88" TYPE="swap" 
archy@archy-desktop:~$ 

can you explain how to change the UUID number? 
About that sda - my swap partition is already on sda2.

---

### Post by WorMzy on 2011-07-03
Press Ctrl+F2, type
```
gksu gedit /etc/fstab
```
press enter and enter your password when prompted.

In the opened file, modify the swap line so that it reads:

```
UUID=1a85f554-f315-4fbc-a3c6-1beb22f7ae88 none swap sw 0 0
```

Save the file, and close the text editor.

Next time you boot up, the swap partition will be automatically used.

---

### Post by HermanAB on 2011-07-03
BTW, something totally non-obvious:
Everything about swap is in the swapon man page:
$ man swapon

It is a good one - worth a read.

---

