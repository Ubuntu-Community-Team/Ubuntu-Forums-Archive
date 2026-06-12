---
title: "Definitely need help - Wubi not booting Ubuntu."
date: 2011-05-23
forum: General Help
---

### Post by bigdan35 on 2011-05-23
Hey guys, this is my first post and I'm a bit of an Ubuntu virgin. Well, I've had a dabble in Ubuntu before and it was enjoyable, though I panicked when I accidently deleted the bootloader for Windows so I decided to get rid of Ubuntu. Which comes to my next point.

[EDIT] When I deleted the bootloader, I used a Windows 7 Recovery CD which got me back on to the OS - which I think messed up the Ubuntu part of the bootloader [/EDIT]

I've currently tried to install Wubi 5 times now - I've created a dedicated partition of 20gb for it as well. Now it downloads Ubuntu and installs it correctly (from what I can see) but when I come to select Ubuntu on start up (the option IS there).. I get a this black screen:

> [http://dl.dropbox.com/u/5142930/IMG_20110523_235350.jpg](http://dl.dropbox.com/u/5142930/IMG_20110523_235350.jpg)

And unfortunately I don't know what to do afterwards. 


Is there any chance of someone knowing what to do with this? I've read many forums and I don't usually come on to a forum to actually ask for help - but it's time, I want to use Ubuntu! I've always wanted Ubuntu as my main OS.

Thanks,

Dan.

---

### Post by bigdan35 on 2011-05-23
Deleted.

---

### Post by s.fox on 2011-05-24
Threads / Posts merged. Please do not create duplicate posts.

Thank you.

---

### Post by Mark Phelps on 2011-05-24
Sorry no one got back -- but I would advise against installing Wubi to anything but "C:".

Since you already have the ability to create a dedicated partition for Ubuntu, it's better to install it to that partition, instead of using Wubi.

What I would suggest is the following:
1) Boot from the Ubuntu CD and use Partition Editor to format the dedicated partition as Ext4
2) Reboot from the Ubuntu CD and install it to that partition
3) When the PC restarts and you are running Ubuntu, open a terminal and enter "sudo update-grub".  That will generate a GRUB menu with entries for Ubuntu and Windows.

When you then reboot, you should see a menu allowing you to make an OS selection.

---

