---
title: "usb-drive permission problems (write + execution)"
date: 2010-07-25
forum: General Help
---

### Post by manolo_asdf on 2010-07-25
hi, 

I am having access problems with my usb-harddrive (which is auto-mounting). 

1) I cannot execute bash script which are on the drive (even as sudo or root user), though the file has a+x permission.
2) I have to do 'sudo' to be able to write to the disk


How can I change this? I want to have permissions to run scripts and have write access to usb-drive. As far as I remember problem 1) turned up first time after upgrading to 10.04. Did something change with automounting usb-drives? 

thanks.

---

### Post by AlphaLexman on 2010-07-25
Is the 'usb-drive' (external) how is it formatted (ext3, ext4, fat, ntfs)?

---

### Post by TeoBigusGeekus on 2010-07-25
```
sudo fdisk -l
```
to find the mount point of your device and then 
```
sudo chown yourusername /media/mountpoint
```
to change ownership of the device.

---

### Post by manolo_asdf on 2010-07-25
@AlphaLexman:
> **AlphaLexman said:**
> Is the 'usb-drive' (external) how is it formatted (ext3, ext4, fat, ntfs)?

the formatting is fat32:

```

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

```


@TeoBigusGeekus: your tips didn't help. Really weird why...
```

manuel@manolo:/media/usb/backups/private/blog$ sudo chown  manuel /dev/sdc1
manuel@manolo:/media/usb/backups/private/blog$ cat bla
#!/bin/bash
echo hello	
manuel@manolo:/media/usb/backups/private/blog$ ls -la bla 
-rwxr-xr-x 1 root root 24 2010-07-25 21:47 bla
manuel@manolo:/media/usb/backups/private/blog$ ./bla
bash: ./bla: Permission denied

```

---

### Post by mc4man on 2010-07-25
edit : wrong assumption

Works fine on lucid - isn't on maverick - need to look at why

---

### Post by AlphaLexman on 2010-07-25
Fat32, fat16, or ntfs do NOT store unix / linux file permissions. The file permissions are 'assumed' by the daemons that read those file-system-types. Ext3 and ext4 are the newer file-system types found on linux / ubuntu. 

QUESTION: Why do you have bash executable scripts on a non-compliant format?
Move or copy the scripts to your ~/ (home) directory and set permissions and execution tags with 'chmod'

A good practice is to have a /home/bin/ directory and add it to your $PATH variable, you can put your important scripts there.

---

### Post by mc4man on 2010-07-25
> Fat32, fat16, or ntfs do NOT store unix / linux file permissions. The file permissions are 'assumed' by the daemons that read those file-system-types. Ext3 and ext4 are the newer file-system types found on linux / ubuntu.

QUESTION: Why do you have bash executable scripts on a non-compliant format?
Move or copy the scripts to your ~/ (home) directory and set permissions and execution tags with 'chmod'

A good practice is to have a /home/bin/ directory and add it to your $PATH variable, you can put your important scripts there. 

All true and good points but..
if for some reason one wanted to run a script from a usb drive that was formatted  vfat or ntfs they can and should be able to do so, at least thru lucid.

maverick is no longer allowing that to happen, not sure why yet.

@manolo_asdf
with the drive connected run  in a terminal
mount
What are the mount options shown for the usb drive?

---

### Post by mc4man on 2010-07-25
While I don't think this is your issue (may be specific to current udisks in  maverick, 
> What are the mount options shown for the usb drive? 

If you see what I've marked in blue then you won't be able to execute a script on a vfat usb drive

> type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,[COLOR="Blue"]showexec[/COLOR],flush)

This is the result of a patch to prevent all text files on vfat from being seen as executable.

---

