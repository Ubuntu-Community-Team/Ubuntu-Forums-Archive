---
title: "Ubuntu keeps trying to mount Windows partition, but errors"
date: 2010-09-18
forum: General Help
---

### Post by mrinehart93 on 2010-09-18
For some reason, whenever I boot Ubuntu, it tries to mount my Windows partition. It is able to mount my Data partition, which is NTFS as well, just fine. However when it's attempting to mount the Windows partition, it gets an error while it's booting, and give me the option "Press S to skip, or M for Manual Recovery". It's not a big deal to me, but it's annoying that I have to be next to the computer while it's booting to make sure it boots properly. Can anyone help me out here? Thanks!

---

### Post by lmarmisa on 2010-09-18
Open a terminal, type this command and post the output:

> 
cat /etc/fstab


---

### Post by mrinehart93 on 2010-09-18
mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid             0  0  
# / was on /dev/sda5 during installation
UUID=def9d945-19b1-42e9-b9dd-855f98d86e29  /               ext4  errors=remount-ro               0  1  
# swap was on /dev/sda6 during installation
UUID=2a088560-0120-486a-9650-08866c0c6b12  none            swap  sw                              0  0  
/dev/sda2                                  /media/Windows 7  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda3                                  /media/Data     ntfs  nls=iso8859-1,umask=000         0  0  
/dev/sda2                                  /media/windows  ntfs  nls=iso8859-1,noauto,umask=000  0  0  
/dev/sda1                                  /media/sda1     ntfs  defaults                        0  0  
mike@mike-desktop:~$

---

### Post by DeMus on 2010-09-18
> **mrinehart93 said:**
> mike@mike-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid             0  0  
# / was on /dev/sda5 during installation
UUID=def9d945-19b1-42e9-b9dd-855f98d86e29  /               ext4  errors=remount-ro               0  1  
# swap was on /dev/sda6 during installation
UUID=2a088560-0120-486a-9650-08866c0c6b12  none            swap  sw                              0  0  
/dev/sda2                                  /media/Windows 7  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  
/dev/sda3                                  /media/Data     ntfs  nls=iso8859-1,umask=000         0  0  
/dev/sda2                                  /media/windows  ntfs  nls=iso8859-1,noauto,umask=000  0  0  
/dev/sda1                                  /media/sda1     ntfs  defaults                        0  0  
mike@mike-desktop:~$

Could it be the space in the name "Windows 7"? Replace that with Windows7 for example and of course also change the name of the folder in /media the same way.

---

### Post by mrinehart93 on 2010-09-18
Ok, I'll try that right now DeMus. I'll report back with results.

---

### Post by lmarmisa on 2010-09-18
This link could help you:

[http://en.kioskea.net/faq/2287-fstab-adding-spaces-in-the-mount-point-path](http://en.kioskea.net/faq/2287-fstab-adding-spaces-in-the-mount-point-path)

---

### Post by mrinehart93 on 2010-09-18
Thanks DeMus, your suggestion worked! 

I simply did a "sudo gedit /etc/fstab", and removed the space in Windows 7. Then I went to /media, browsed it as root, and then noticed that there was a Windows7 folder and a Windows 7 folder. I made the assumption that editing fstab generated the Windows7 folder, so I deleted the Windows 7 folder. I rebooted, and there were no errors! Thanks for the help guys!

---

### Post by DeMus on 2010-09-18
Mark the thread as solved please so others know this is a thread with a working answer.

---

