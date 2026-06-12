---
title: "grub won't boot"
date: 2011-10-01
forum: General Help
---

### Post by Oxyris on 2011-10-01
okay so i installed ubuntu 11.04 onto my logical partition. Idk if it worked, grub won't boot. When I rebooted it went straight to windows, no grub, tho I did get a screen that said disk was changed and was trying to analyze the disk for errors. I rebooted again and hit f2 and got what i assume was windows bootloader with only the option of windows. So I don't know where grub is or if my ubuntu partition was successful. Disk manager does tell me two new partitions were made (see picture). So did I do something wrong? Is there any way to get grub to show up?

---

### Post by amjjawad on 2011-10-01
> **Oxyris said:**
> okay so i installed ubuntu 11.04 onto my logical partition. Idk if it worked, grub won't boot. When I rebooted it went straight to windows, no grub, tho I did get a screen that said disk was changed and was trying to analyze the disk for errors. I rebooted again and hit f2 and got what i assume was windows bootloader with only the option of windows. So I don't know where grub is or if my ubuntu partition was successful. Disk manager does tell me two new partitions were made (see picture). So did I do something wrong? Is there any way to get grub to show up?

Hi,

You have 5 partitions, 4 of them are primary? how come?
Am I seeing that correctly?

---

### Post by Oxyris on 2011-10-01
> **amjjawad said:**
> Hi,

You have 5 partitions, 4 of them are primary? how come?
Am I seeing that correctly?
*i'm booted into the live cd right now and disk utility is telling me that the linux partition and the  swap partition is under the windows extended partition. i'm guessing that's  bad. I tried reinstalling grub according to this link*[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2) and I got the following 

ubuntu@ubuntu:~$ sudo mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda6/mnt
mount: can't find /dev/sda6/mnt in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: /dev/sda6 already mounted or /mnt busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda6
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

---

