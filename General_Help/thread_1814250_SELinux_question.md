---
title: "SELinux question"
date: 2011-07-29
forum: General Help
---

### Post by unix1adm on 2011-07-29
I decided to load SELinux on one of my systems last night. Now I am use to using it in the RH/CentOS world. 

However I thought this was strange. I loaded it and put it in enforcing mode. 

When I went to shut the system down it would not. It only logged me out. I had to put it back to Permissive mode to get the system to shutdown. 

Also I don't see a GUI for it in the menus options any place. 
In RH there is a UI for it. 



I was logged in as my local ID and had to sudo to put it in enforcing or permissive. 

I could shut the box down as root if I issued the shutdown command. But as my user I cannot. 

What am I missing?

---

### Post by unix1adm on 2011-07-31
[so i guess no one uses selinux on Ubuntu. Google has not proved to helpful either. 

Ill keep searching.

---

### Post by unix1adm on 2011-08-18
Still no comments. wow. I would think someone else had run into this issue. 
I am still having problems with it but have removed it for now.

---

### Post by Ghion on 2011-08-21
Same here. Struggling with SELINUX for a week now. When turning enforce mode to enforcing during run time i cannot log out. If i turn to enforcing with selinux-config-enforcing at  boot time it boots only in error console with no graphics. If i delete the file config in /etc/selinux then i can reboot normally. That file contains the setting SELINUX=permissive or SELUNUX=enforcing.

Still a bit confused about the difference between Selinux and Selinux basics.

Found out about audit2allow and auditd which are not installed on ubuntu. audit2allow parses the log files and generate te files (type enforcement) that can be edited and then turned into pp or mod files.

This is where i'm at please tell me if you try to go further with some results.

And yes, nobody is using Selinux on Ubuntu.

I'm wondering if Apparmor has major problems that you know of and why you wanna switch.

Considering giving up and trying something like Fedora which apparently works with Selinux and has default policies installed for many applications.

---

