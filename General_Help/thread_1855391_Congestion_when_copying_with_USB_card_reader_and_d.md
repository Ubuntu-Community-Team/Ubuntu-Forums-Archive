---
title: "Congestion when copying with USB card reader and dd"
date: 2011-10-06
forum: General Help
---

### Post by tripialos on 2011-10-06
Hi Everyone.

I would like to discuss an issue i am facing quite often at work when trying to copy raw images (.img) on Compact Flash disk.

See, we copy CentOS images on CF (compact Flash Disks) and the way we do that is by connecting a usb card reader, insert the CF disk on the reader and then issue the command

```
$dd if=CentOS.img of=/dev/sdb
```

Now what is the problem? Until the copying is finished the system is "going" reeeeally slow. It feels like the whole CPU and Memory is full and 100% in use.

I click on a window on my panel and takes like 2 sec to come up. Takes like 30 sec to start up an other software.

All the above stop when the copying is done. The system is back to normal when the dd process is finished.

This is quite strange because i haven't met that problem in older versions of Ubuntu and on the "you know which other operating system" i do not meet this kind of problems.

Any ideas?
Any thoughts? 

My Specs:

PC:  HP probook 4320s
CPU: i3 2.5GHz
RAM: 3GB

Thanks in Advance

---

