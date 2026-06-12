---
title: "space on root partition mysteriously disappearing"
date: 2010-10-19
forum: General Help
---

### Post by maja_z on 2010-10-19
I'm not sure if I can even explain this properly! I'm attaching a hopefully self-explanatory screenshot of
(1) system monitor saying that 23.3 out of 24.6 GB of my root is used (!!!)
(2) diskanalyzer showing root should be 5.9+4+3.3+some small stuff = about 15 GB.

At startup I get a warning saying something along the lines of "you only have 50MB available on root file system.. you should delete unnecessary files.. " and that opens Disk Usage  Analyzer. 

Possible suspect - I had been trying out VirtualBox. On root. My virtual machine did have an 8gig hard drive, expandable I believe. But it never got past 1.7, and I've removed it, uninstalled VB and removed it from trash. (Is this weird: my trash is at /home/me/.local/share/Trash/files - took me a hell of a while to find it!) 

With 100MB available on root I can barely do anything! My whole compiz/config setup even disappeared after a reboot!

Any ideas are welcome!
m.

---

### Post by drs305 on 2010-10-19
Take a look at this thread for help finding out where your space is going:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

It provides both command line and GUI methods for searching out the problem.

Often it is unemptied trash bins (Root also has one at /root/.local/share/Trash), backups mistakenly made on the system partition instead of the backup partition because the backup partition wasn't mounted, and large log files.

It helps to umount all non-system drives when trying to find out what is taking up the space. And Disk Usage Analyzer can be misleading - the top level will always show 100%.

---

### Post by maja_z on 2010-10-19
Aw, it was the root/.local/share/Trash one! With everything I had already deleted from the other trash :(

I just don't get why the disk analyzer doesn't see it! I mean if I'm going to get a warning I need to do something about low disk space, it's not very useful if it then opens a utility that then doesn't see the offending trash!

Anyway, cheers drs305 for your quick help!

---

### Post by drs305 on 2010-10-19
I guess the 'logic', if you want to call it that, is that as a user you normally won't have control over things belonging to root. And as a user you wouldn't be able to put anything into root's trash bin. 

In a large organization, it makes sense. For single user or home computers, as you know, we assume admin powers often to accomplish tasks and maintain control over many aspects of our computers, and these actions aren't totally transparent and sometimes create problems such as you experienced. 

If you have your disk space back and don't have any other inputs, would you please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing.

---

### Post by maja_z on 2010-10-19
In my case the lack of transparency of my actions is simply a reflection of not really knowing what I'm doing in the first place :) 

Thanks though, to you and everyone else here that is always so helpful when I abuse my sudo powers!

---

