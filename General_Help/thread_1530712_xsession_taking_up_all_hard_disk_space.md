---
title: "xsession taking up all hard disk space"
date: 2010-07-14
forum: General Help
---

### Post by slooksterpsv on 2010-07-14
This has happened to me twice now and I need to know what's going on. So my computer said that I was out of disk space, checked the file xsession and it was over 80GB. I was in a terminal and tried to remove it, but after removing it I was still out of disk space, I removed it with 

rm .xession-errors

Is there a bug for this or do you know why this happens:
```

Linux shawn-ubuntu-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

```

---

### Post by bodhi.zazen on 2010-07-14
That is one huge x session.

Are you sure your disk is full because of X ?

Check your Trash, check you logs.

---

### Post by slooksterpsv on 2010-07-14
> **bodhi.zazen said:**
> That is one huge x session.

Are you sure your disk is full because of X ?

Check your Trash, check you logs.

Uhh.. what logs, also I restarted so the disk space is normal now, usage is only 14%. Trash was empty, I had to restart to reclaim the space after removing the file.

The file that was taking over 80GB was .xsession-errors - I'm not sure what that is or what it's for, but it was over 80GB - I know cause I ran a ls -lah on my home directory and removed it. I also looked in Disk usage Analyzer and it said my home partition was using 89.5GB and after I did the rm to the .xsession-errors file it said my home was using only 4.6GB

---

### Post by bodhi.zazen on 2010-07-14
> **slooksterpsv said:**
> Uhh.. what logs, also I restarted so the disk space is normal now, usage is only 14%. Trash was empty, I had to restart to reclaim the space after removing the file.

The file that was taking over 80GB was .xsession-errors - I'm not sure what that is or what it's for, but it was over 80GB - I know cause I ran a ls -lah on my home directory and removed it. I also looked in Disk usage Analyzer and it said my home partition was using 89.5GB and after I did the rm to the .xsession-errors file it said my home was using only 4.6GB

Well, I would try to figure out what is causing those errors.

```
tail ~/.xsession-errors
```

As far as logs, they are kept in /var/log and they can also get large if you are having frequent error messages.

If you do not know how to read the logs, see : [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by slooksterpsv on 2010-07-19
HAHA I got proof booya!

Anyways the xsession-errors.old file is 895M, and I've shown the tail of it too - here's a screenshot.

Problem is with Cairo.Context - if that's for Cairo Dock I don't have that one installed, I'm using Docky, which I love.

So how can I fix this? Do I need to patch some files or just remove docky or is it a problem with an icon on the dock? Cause I have (in order):

Docky:Firefox:Empathy:Evolution:RhythmBox:Eclipse:Terminal:VirtualBox:TeamViewer::Time/Date:Weather:Trash

---

