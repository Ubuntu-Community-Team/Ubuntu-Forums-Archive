---
title: "diskspace full gvfs likely culprit"
date: 2010-09-11
forum: General Help
---

### Post by roboa1983 on 2010-09-11
Hello:
I don't want to rush into conclusions, but I have this problem that I have not been able to solve. 
This morning I found that my diskspace was full. After being mildly surprised, I went to erase a big portion of it (~60 GB). Interestingly, a couple of hours later the disk was full again and I definitely did not save as much.
As I deleted other directories, I noticed that the free space was not getting larger, but rather it remained constantly close to zero. There seemed to be a vino-server app which I killed. 
Later, space got stable at around 1 GB. I analyzed the disk space with baobab and it showed that my home directory was full (df gives the same result), but on a closer inspection (check png file attached), the maximum directory has only 45 GB. The only place that baobab cannot access is .gvfs directory (running baobab on sudo)

```

** (baobab:2453): WARNING **: error in dir /home/roberto: Error stating file '/home/roberto/.gvfs': Permission denied

```

So I am assuming that the remaining diskspace is located there. However, du states the directory has exactly 0 bytes. 

This problem has shown up in different form before, but none of the answers seem to help out in my case.

I'd appreciate any ideas to solve this.

Thanks!

---

### Post by robsoles on 2010-09-12
.gvfs is a special folder that should not take up space on your local computer file system.

Does [http://www.linux.com/archive/feed/51600](http://www.linux.com/archive/feed/51600) help?

---

### Post by JBAlaska on 2010-09-12
Have you checked your log files in ```
/var/log/
```syslog, kern.log, messages and ufw.log can grow to huge sizes in a short time if there is a persistent error or event being logged.

---

### Post by roboa1983 on 2010-09-12
Hi!
Thanks for the replies. I did use du and df along with baobab to assess the diskspace. Furthermore, /var/log was reasonable in size. 
All of this was showing that my /home directory had 100% of the diskspace, but I could only account for about 50% of so. The rest did not appear in the results of the programs above (du or baobab). The only place these could not access what .gvfs
After a second restart, things got back to normal and it appears all the diskspace is correctly accounted for.
So I guess this problem got fixed, but without knowing the underlying reasons.

---

### Post by drs305 on 2010-09-12
Boabab can be a bit confusing. The top folder always shows 100%, even when it's not full.

If you want to look at some more aspects of investigating disk space, here is the link to a post I made about it. It covers deleting/trash bins, backups made to the wrong folder, large log files, etc. 

For instance, when I first read your post I thought it might be a delete problem, since deleting files doesn't free up any disk space until you empty your trash bin.  Anyway, here is the link:

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by roboa1983 on 2010-09-13
> **drs305 said:**
> Boabab can be a bit confusing. The top folder always shows 100%, even when it's not full.

If you want to look at some more aspects of investigating disk space, here is the link to a post I made about it. It covers deleting/trash bins, backups made to the wrong folder, large log files, etc. 

For instance, when I first read your post I thought it might be a delete problem, since deleting files doesn't free up any disk space until you empty your trash bin.  Anyway, here is the link:

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

drs305: Yes, I looked into that, but df still said I was at 100% capacity, so baobab and df agreed in giving this false positive

It will be hard to assess what the problem was right now since it disappeared, but reading from your guide I believe it was related to issue g in the guide you mentioned. I believe I did read through it while I was trying to fix this problem, but to no avail...
In any case, thanks for the response and will be on the lookout in case this problem shows up again.

---

### Post by xircon on 2010-09-13
I prefer kdirstat to all the standard gnome programs.  It is similar to windirstat and is easier to read than baobob:

---

### Post by roboa1983 on 2010-09-13
> **xircon said:**
> I prefer kdirstat to all the standard gnome programs.  It is similar to windirstat and is easier to read than baobob:

Xircon: I'll check it out. I don't use many KDE programs to often, except okular. Let's see if kdirstat is able to assess this next time.

---

### Post by xircon on 2010-09-13
I run a selection of what suites me, was die-hard KDE, now run what I like on a heavily modified Gnome (running on top of KDM) a real mongrel!!!

PS it doesn't (on my machine) make a menu entry, run with alt-f2

---

