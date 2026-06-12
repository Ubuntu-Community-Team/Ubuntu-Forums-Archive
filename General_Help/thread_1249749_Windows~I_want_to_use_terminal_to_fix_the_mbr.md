---
title: "Windows~I want to use terminal to fix the mbr"
date: 2009-08-25
forum: General Help
---

### Post by KEE on 2009-08-25
I want to know the commands in terminal for ```
>root noverify (hd0,0)
> Chainloader +1 
``` I tried the a /mbr disk but the disk wont load for me to set it back to windows. I am only assuming that the /mbr is broke. I got this error when i tried to install Intrepid ```
 	DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Cannot mount volume 
Details
$LogFile  indicates unclean shutdown (0, 0) Failed to mount '/ dev/sda1'; Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line:  mount -t ntfs-3g/ dev/sada1 /media/disk-1 -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1/media/ disk-1 ntfs-3g force 0 0  

```please help

---

