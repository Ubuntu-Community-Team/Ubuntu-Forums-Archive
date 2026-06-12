---
title: "Available space in a partition not updating"
date: 2011-08-11
forum: General Help
---

### Post by subhacom on 2011-08-11
A 550 GB data partition on my hard disk became full. But after deleting a 150 GB file (a log from a nohup-ed program still running) using rm, when I run

```
df -h
```as ordinary user, it still shows:

/dev/sda7             581G  551G  386M 100% /data

However, it gives me the correct usage when I run 

```
du -sh /data
```as root:

408G    /data/

Also, if I try to write some files to the partition, it fails with the message:

error: file write error (No space left on device)

Is this happening because nohup is holding on to the handle to the deleted log file? Is there any way around without killing the nohup-ed program?
I am using Ubuntu 10.04, 64 bit.

---

### Post by terry_a_g on 2011-08-11
That's exactly what is happening.  The running program still has a reference to the file open.  You'll probably have to restart the process.  In the future, the logrotate command or echo "" > yourlogfile to truncate the logfile instead of deleting it may be of use if the program is written correctly and is writing to the file in append mode.

---

