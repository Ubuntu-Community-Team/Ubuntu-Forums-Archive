---
title: "Dual Boot w/ DropBox: Ubuntu + Windows XP"
date: 2009-10-08
forum: General Help
---

### Post by 1awesomeguy on 2009-10-08
Hey Guys,

I have Ubuntu and WinXP running as duel boot. I just installed DropBox and have been thinking of upgrading to a larger plan if I get this to work. Basically, DropBox syncs all files on my Ubuntu /home/USER/Dropbox directory with their online server. DropBox on WinXP by default syncs all files in the ..../My Documents/DropBox directory. 

I use Ubuntu a lot more so would prefer to have that be the default DropBox folder. How can I get Windows to recognize my /home/USER/DropBox folder? I can currently mount the WinXP partition in Ubuntu, but cannot do the opposite.

Is there a way I can link both folders so they do not take up twice the amount of space?

I am a big Linux newbie so any help would be really appreciated!

---

### Post by howefield on 2009-10-08
> **1awesomeguy said:**
> Is there a way I can link both folders so they do not take up twice the amount of space?

Create an Ntfs partition for your dropbox files, and point dropbox to it ?

---

### Post by jeremyswalker on 2009-10-08
There are a few add-ons for windows that may help you. They are Explore2fs, DiskInternals Linux Reader, and Ext2 Installable File System for Windows. I personally do not have any experience using any of them. However, in my experience, using non-native file systems can cause corrupt data. I'm not saying it is a common thing, but it has happened to me in the past. Just be careful, and research the solutions before you implement them.

---

### Post by jeremyswalker on 2009-10-08
Actually, howefield has a good idea. Format a partition using NTFS or FAT32 and use that for Dropbox.

---

### Post by howefield on 2009-10-08
> **jeremyswalker said:**
> There are a few add-ons for windows that may help you. They are Explore2fs, DiskInternals Linux Reader, and Ext2 Installable File System for Windows.

I was going to mention these solutions, but I don't think I have ever read anything (testimonials/reviews) that speaks really well about them. And certainly didn't enjoy the one time I tried them.

*"You pays yer money and takes yer choice...."*

Having said that, someone is bound to come along and say they are the best thing since... whatever ;)

---

### Post by 1awesomeguy on 2009-10-08
Thanks for the suggestions.

My Windows partition is already NTFS. Should I just use the default folder location DropBox uses in WinXP? It would save me some time than having to redistribute the small amount of space I have on my laptop. What would be the best solution?

Would Ubuntu auto-mount the partition when I log in?

---

### Post by howefield on 2009-10-08
> **1awesomeguy said:**
> Should I just use the default folder location DropBox uses in WinXP?

Yes, that would be fine.

> Would Ubuntu auto-mount the partition when I log in?

Should do, but if not, it is easy enough to make it do.

Tutorial with pics....

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by 1awesomeguy on 2009-10-08
Thanks howefield! Very useful tutorial. I think I will go ahead and create a sperate parition just to keep things nice and neat. That tutorial will come in handy though!

---

