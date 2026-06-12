---
title: "login problem - Gnome power manager config"
date: 2010-09-10
forum: General Help
---

### Post by joneslh on 2010-09-10
After running a backup script, but previously deleting old downloads and files from the rubbish bin, I then logged out.

When logging back in later I got the Ubuntu loading screen as normal, but then instead of the Ubuntu login I got another login screen that I have not seen before; black background with the login screen in the middle.

I tried to login in, but all I got was an error message saying  'Install problem - The configuration defaults for Gnome power manager have not been installed correctly !!!!

I am running Ubuntu 10.04 and had a stable system.  Can anyone help with this problem.

---

### Post by joneslh on 2010-09-10
after browsing various forums, I think my problem is the my Sda6 partition is full.

Whilst trying various purges and then re-installs of the Gnome Power manager, I find that I get message after 'processing triggers for man-db'

/usr/bin/mandb: can't write to /var/cache/man/8653: No space left on device 

Anyone any thoughts on how to proceed ?

After further exploration of my system I find that I have the following devices -

/dev/sda1   ID 7   HPFS/NTFS
/dev/sda2   ID 83  Linux
/dev/sda3   ID 5   Extended
/dev/sda5   ID 82  Linux swap/Solaris
/dev/sda6   ID 83  Linux
/dev/sda7   ID 82  Linux swap/Solaris

I should not have two Linux and Linux swap devices.  I think this may be the result of downloaded an early release of 10.04 which crashed my system and a I have to reload 9.04.

What is the best way to remove the unwanted devices ?



I have solved my problem by finding and deleting the large backup file that had completly filled my Ext4 partition.  This was done using a live Linux CD from a Linux magazine to search the folders.  Once found, I then used the boot recovery mode to remove the offending file and all is back to normal.  

Now I need to look at re-sizing my Ext4 partition.

---

