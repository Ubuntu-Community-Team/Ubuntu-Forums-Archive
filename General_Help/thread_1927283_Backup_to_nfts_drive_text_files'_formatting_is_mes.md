---
title: "Backup to nfts drive: text files' formatting is messed up."
date: 2012-02-17
forum: General Help
---

### Post by vincegata on 2012-02-17
Hello,

I backup my files on external ntfs drive. Now, when I restore files back to Ubuntu running on ext4:

1) Text files' formatting is all messed up. 

2) Scripts that were marked as executable are not executable anymore.

Does someone know how to fix this?

Thank you!

---

### Post by ajgreeny on 2012-02-17
Backup as an archive file of some sort, eg tar.gz, then all the files in that archive should retain their permissions which ntfs can not retain on files, but which are retained on files in an archive.

Use rsync or grsync to backup and you can make the archive automatically.

---

### Post by vincegata on 2012-02-17
I use rsync for backups but I do not use any special archive formats I just backup files (incremental backup). This way I can see the files that I backup up and easily restore separate files instead of the whole archive.

---

### Post by dcstar on 2012-02-18
> **vincegata said:**
> Hello,

I backup my files on external ntfs drive. Now, when I restore files back to Ubuntu running on ext4:
.......

NTFS is **not** a Linux filesystem, it does not support Linux attributes (as well as many other things) and **cannot** be used to backup Linux files.

Backup Linux filesystems to other Linux filesystems, not crappy Windows ones.

---

### Post by vincegata on 2012-02-18
We have both OSs (Ubuntu and Win7) at my household hence the backup drive is ntfs. 

I understand why executable flag is gone when I restore script files, but why the formatting in text files gets messed up? It's all ANSI coding after all.

---

### Post by matt_symes on 2012-02-18
Hi

> **vincegata said:**
> We have both OSs (Ubuntu and Win7) at my household hence the backup drive is ntfs. 

I understand why executable flag is gone when I restore script files, but why the formatting in text files gets messed up? It's all ANSI coding after all.

Windows uses different line ending characters the Linux. Linux uses a line feed and Windows uses carriage return and line feed.

So if you open a file created in Linux in Notepad on Windows, it will look messed up.

Is this what is happening ?

Kind regards

---

### Post by vincegata on 2012-02-18
I create a text file in gedit in Ubuntu, then I backup the file on ntfs drive, then I restore the file back to Ubuntu, now I open the file in gedit and it's messed up.

---

### Post by coffeecat on 2012-02-18
> **vincegata said:**
> I create a text file in gedit in Ubuntu, then I backup the file on ntfs drive, then I restore the file back to Ubuntu, now I open the file in gedit and it's messed up.

This doesn't happen to me using an ordinary drag and drop copy to an external NTFS drive and back again, so I wonder if there's some issue with rsync and ntfs. Try an ordinary single file copy and back again and see what happens.

---

### Post by vincegata on 2012-02-18
right... when I manually copy it is alright. But when I used rsync earlier to backup / restore it looks like this. It's small part of one of my text files (the comments after pound sign should be aligned). I guess I need to do some investigation on rsync. Thank you for the tips.

```

uptime						# For how long the system has been running.
hostname													# Gives the name of a host you are working on.
sudo lshw -short											# List hardware
startx														# start X-Window session
sudo update-alternatives --config java						# set default Java to use
java -version												# check the version of java

```

---

