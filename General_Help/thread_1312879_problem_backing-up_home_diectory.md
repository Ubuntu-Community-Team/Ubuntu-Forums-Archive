---
title: "problem backing-up /home diectory"
date: 2009-11-03
forum: General Help
---

### Post by yanvolking on 2009-11-03
Hello Community,

I would like to make a backup copy of my home directory.  Here are the results of 2 command line approaches :

yan@yan-acer:~$ cp /home /media/16GB_USB/091103_acer_home_directory
cp: omitting directory `/home'
yan@yan-acer:~$ rsync /home /media/16GB_USB/091103_acer_home_directory
skipping directory home
yan@yan-acer:~$ 


Why is my /home directory omitted?  What can I do to get around this problem?

thanks

---

### Post by Giblet5 on 2009-11-03
Is /media/16GB_USB an ext3/4 file system?

FAT32 - the standard USB filesystem - does not preserve linux file permissions and ownership. Bad Idea.

Try this instead: ```
sudo tar -czvf /media/16GB_USB/MyHomeBackup.tar.gz /home
```

To restore: ```
cd /
sudo tar -xzvf /media/16GB_USB/MyHomeBackup.tar.gz
```

To list: ```
tar -tzf /media/16GB_USB/MyHomeBackup.tar.gz
```

WinZip and WinRar can read that file under Windows too.

---

### Post by yanvolking on 2009-11-03
Hi and thanks for the advice.  You are right, 16GB_USB is a USB device formatted in FAT32.

I did what you suggested and this is what happened:

yan@yan-acer:~$ sudo tar -czvf /media/16GB_USB/MyHomeBackup.tar.gz /home
[sudo] password for yan: 
tar: Removing leading `/' from member names
/home/
/home/yan/
/home/yan/.Xauthority
tar: /media/16GB_USB/MyHomeBackup.tar.gz: Cannot open: Input/output error
tar: Error is not recoverable: exiting now
/home/yan/.mozilla/
/home/yan/.mozilla/extensions/
/home/yan/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/
/home/yan/.mozilla/firefox/
/home/yan/.mozilla/firefox/hzb9uk8y.default/
/home/yan/.mozilla/firefox/hzb9uk8y.default/secmod.db
yan@yan-acer:~$ 

What went wrong?  I must admit I am not familiar with the "tar" category of commands....but sounds a powerful tool.

thanks

---

### Post by Commander_Keen on 2009-11-03
You know what you may want to do.
  Just copy and past your home folder to the USB drive.
that's how I backup my home folder,

---

### Post by Giblet5 on 2009-11-03
> **yanvolking said:**
> Hi and thanks for the advice.  You are right, 16GB_USB is a USB device formatted in FAT32.

I did what you suggested and this is what happened:

yan@yan-acer:~$ sudo tar -czvf /media/16GB_USB/MyHomeBackup.tar.gz /home
[sudo] password for yan: 
tar: Removing leading `/' from member names
/home/
/home/yan/
/home/yan/.Xauthority
tar: /media/16GB_USB/MyHomeBackup.tar.gz: Cannot open: Input/output error
tar: Error is not recoverable: exiting now
/home/yan/.mozilla/
/home/yan/.mozilla/extensions/
/home/yan/.mozilla/extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}/
/home/yan/.mozilla/firefox/
/home/yan/.mozilla/firefox/hzb9uk8y.default/
/home/yan/.mozilla/firefox/hzb9uk8y.default/secmod.db
yan@yan-acer:~$ 

What went wrong?  I must admit I am not familiar with the "tar" category of commands....but sounds a powerful tool.

thanks


Root doesn't have permission to write to /media/16GB_USB/MyHomeBackup.tar.gz

Either the device is mounted read-only or the directory /media/16GB_USB is marked read-only.

You have to be allowed to write to it before you can do backups on it. It isn't full is it?


> **Commander_Keen said:**
> You know what you may want to do.
  Just copy and past your home folder to the USB drive.
that's how I backup my home folder,

If you never want to recover all of your files, that will make some of them available, yes.

FAT32 loses file permission and ownership data. That's what archiving programs like "tar" and "cpio" are for.

---

### Post by zzzBrett on 2009-11-03
> **yanvolking said:**
> Hello Community,

I would like to make a backup copy of my home directory.  Here are the results of 2 command line approaches :

yan@yan-acer:~$ cp /home /media/16GB_USB/091103_acer_home_directory
cp: omitting directory `/home'
yan@yan-acer:~$ rsync /home /media/16GB_USB/091103_acer_home_directory
skipping directory home
yan@yan-acer:~$ 


Why is my /home directory omitted?  What can I do to get around this problem?

thanks

I thought it omits the directory if you do not add the -R argument?

---

### Post by Giblet5 on 2009-11-03
> **zzzBrett said:**
> I thought it omits the directory if you do not add the -R argument?

That's only one of many problems with doing a backup that way.

The biggest problem is that neither command will perform the desired task, even if the command line arguments are corrected.

The tar command is easy to learn, it's reliable, it provides error recovery, it saves everything, it can compress (a lot), it's found on any Unix-like system, and WinZip and similar Windows software can read/use its archives directly.

At the end of the day, that which works is what one should do.

---

### Post by yanvolking on 2009-11-04
OK guys, Thanks for all your help.  It finally all clicked.  I now understand the fundamentals of the TAR command (impressive tool).  For the rest I'll manage to get by with the various datasheets available on the net.

Yan

---

