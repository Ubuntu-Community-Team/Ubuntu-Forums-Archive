---
title: "RabbitVCS too slow on big resporities"
date: 2010-10-16
forum: General Help
---

### Post by SoulSmasher on 2010-10-16
Hi, I'm suffering from an issue of RabbitVCS.

I need to follow a big SVN respority, which has about ~20k files (or more), and when I click on the folder, nautilus just freezes for a while because of RabbitVCS.

I'm using ubuntu 10.10 x64, using the very last RabbitVCS froum launchpad, and I've 4gb of ram so memory should not be an issue I guess.

What may cause this ? How Can I fix it, or is there an good alternative SVN browser except KdeSVN and RapidSVN?

Thanks

---

### Post by SoulSmasher on 2010-10-16
*bump any ideas?*

---

### Post by SoulSmasher on 2010-10-17
OK found a good client for my needs

pysvn

thanks anyways..

---

### Post by phaedrus54 on 2010-10-24
RabbitVCS did a write-up about why it's so slow with large repositories (in their blog).

Sounds like its a problem with Nautilus using a single thread and there's currently no good solution :(.

PS- Did you need to do anything special with the install in 10.10 x64 Ubuntu? I've been having trouble doing simple tasks, ie committing and updating. The commit window seems to stall and won't complete the task.

---

### Post by phaedrus54 on 2010-10-24
After another hour or so of playing with it I found this guide that solved my problems: [http://systhread.net/texts/200607subver.php](http://systhread.net/texts/200607subver.php)

Just had to start in commandline and setup SVN, edit basic config files, then I can use RabbitVCS to maintain my own small repo. Gedit plugin looks handy.

Hope your py*svn works well.

---

