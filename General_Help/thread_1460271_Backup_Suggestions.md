---
title: "Backup Suggestions?"
date: 2010-04-22
forum: General Help
---

### Post by xrecar on 2010-04-22
Hey guys, hope you're all doing great.

I've opened this thread to ask you guys about automated backups.

So far, I know there quite a few backup managers in the Linux world that are similar to Apple's time machine and resemble it somehow.

I'm going to go for a clean install of Lucid when it comes out in a week, I don't want to do the straight upgrade for a few reasons that I'm not going to discuss in the thread. I've already decided it.

So, my question is, which backup assistants are good and compatible with Lucid? I would really like to try this out.

Thanks in advance.

---

### Post by Untitled_No4 on 2010-04-22
Hi,

I'm using two clients:
1. SpiderOak ([www.spideroak.com](www.spideroak.com)). They have client for Linux and they give you 2GB free online space to back up your documents to. Over 2GB you will have to pay $10 for up to 100GB of space. Or you can get use the refer a friend scheme and you will get 1GB added to your free account for each friend (up to 5GB). Cons: 1) make sure you don't forget your password as they don't store it and they can't restore it. 2) It's mostly closed source.
2. Time Drive ([http://www.oak-tree.us/blog/index.php/science-and-technology/time-drive](http://www.oak-tree.us/blog/index.php/science-and-technology/time-drive)). Open source client which allows you to to back up to a network device or to your own online. I use it with my unlimited webspace but you can also backup to Amazon cloud. Supports FTP and SSH (and others). It's available from an Ubuntu PPA and although it works well it's still actively developed and the GUI is not 100% polished.

Otherwise, if you want to backup to a device the easiest way is to install Grsync and use it to sync your files to the device.

---

### Post by xrecar on 2010-04-22
Thanks! I'll look into Grsync. 

I forgot to specify that I already have an external HDD, which is where I want to backup.

Keep the suggestions coming.

---

### Post by lukeiamyourfather on 2010-04-22
The best and most basic is always rsync, or cron and rsync for scheduled backup. Grsync is nice but kind of cumbersome if you're familiar with using the terminal. Cheers!

---

