---
title: "File/Folder ownership and permssions problem"
date: 2006-05-11
forum: General Help
---

### Post by jdm2 on 2006-05-11
First off I'm new to linux and ubuntu.  
Second I'm dual booting xp home and ubuntu.  
Third I'm trying to edit a file/folder/volume ownership/permissions.  

I have this sharded drive that I can share files from my xp machine to ubuntu and vise ver.  I can't do anything with it on my account.  In root I can put stuff in and delete it.  I can't change the ownership and permissions in root.  It says I'm not the owner.  I think it's located at /=root(sorry if it's the wrong one) /media/shared.  I took some snapshots of it when it gave me a message so I will try and get it upload soon.  I try to edit it in root and with a command which basiclly brought up a temperary root file browers.  I also tried system tools>run as different user and I ran the file browers as root.  Can you help me out.  Thanks

---

### Post by TLE on 2006-05-11
The answer probably is to change the permissions it is mounted with on boot-up. There is a description of this in the end of [this thread]("http://www.ubuntuforums.org/showthread.php?t=168544").

This info is also available in the starter guide. You can acces it by choosing "help" in the system menu. Here choose "Ubuntu 5.10 Starter Guide". When you are in the starter guide there is a menu on your left, here choose "Windows partitions" and find the section "How do I mount Windows partitions (NTFS) on boot-up, and allow all users to read only?"

BTW it is in general a good idea, for Ubuntu/Linux newbies to read the starter guide, I went through it myself when I started with Ubuntu. It usually gives the answers to alot of questions, some of which I didn't even know I wanted to ask *G*

Hope it fixes your problem. Regards TLE

---

### Post by Googler on 2006-05-11
is it an NTFS partition?

---

### Post by jdm2 on 2006-05-15
It is a fat partition.  It's 135 gb.

---

