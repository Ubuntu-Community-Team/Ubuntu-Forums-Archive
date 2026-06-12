---
title: "Installing ubuntu on main drive"
date: 2010-04-04
forum: General Help
---

### Post by TBhX£2760R8@nK7§r on 2010-04-04
Up untill today, I used XP, but today, I decided to install ubuntu. So far, I have failed, due to me not knowing how to specify the drive ubuntu installs on. I would like it to install on the same drive I have windows installed on, but instead, it insists on installing on the hard drive I have dedicated to downloads. How would I go about fixing this?

Any and all help is greatly appreciated.
Scuzzball.

---

### Post by s_ø on 2010-04-04
Could you be more specific? How are you are trying to install? How does it insist on installing on the specific drive?

---

### Post by TBhX£2760R8@nK7§r on 2010-04-04
I got the newest version today, burned it to a cd, and then rebooted with the cd in the drive. I told it to install, and then it never gave me the option to choose where to install it.

---

### Post by s_ø on 2010-04-04
Does it just hang with a black screen after you select "install ubuntu"?
You never get a screen where you select language, keyboard layout, time zone and so on?

Have you checked the md5 sum of the .iso file you downloaded?

---

### Post by TBhX£2760R8@nK7§r on 2010-04-04
No, I get those. But what I do not get is a way to select where it installs, wherein lies the problem. I want it to install on my main drive. Not a extra drive, where it tries to install, before I quit. This other drive happens to be external.

---

### Post by Silent Warrior on 2010-04-04
For that level of control you will have to use manual partitioning. Or you could always just try to install with the external drive disconnected. That should take care of any confusion on the installer's part. You may have to work some magic later, though, if Ubuntu complains about permissions. But there are ways to tackle that when and if it happens, don't fret.

---

### Post by s_ø on 2010-04-04
Ok. Try to look at this image [http://news.softpedia.com/images/extra/LINUX/large/ubuntu910installation-large_007.jpg](http://news.softpedia.com/images/extra/LINUX/large/ubuntu910installation-large_007.jpg)
When you select "Erase and use entire disk" you only get one option from the dropdown menu?

Try and select "specify partitions manually". What do you see?

Which drive is external? the one you are installing Ubuntu on? otherwise try and unplug it before loading the installer.

The screenshot is from this tutorial on installing Ubuntu 9.10[ http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml]("http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml")

---

### Post by TBhX£2760R8@nK7§r on 2010-04-04
I would like to install ubuntu on the internal hard drive with windows on it. When I select partitions manually, it still only acknowledges one hard drive, the terabyte external. I will try unplugging it and installing now.

---

### Post by TBhX£2760R8@nK7§r on 2010-04-04
Okay. I found the problem, it was, of course, me not looking hard enough. Needed to look in the drop down menu, for the right drive. Now I just need to get a partition on it... Sorry for the idiocy, and thanks for the help.

---

### Post by ajgreeny on 2010-04-04
Maybe a bit late, but look at this page for details, and info on a separate /home partition; highly recommended!
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by s_ø on 2010-04-04
You are welcome. Better to ask than deleta a TB of good stuff.
Check out the link ajgreeny gave you. And mark thread as solved.

---

### Post by TBhX£2760R8@nK7§r on 2010-04-05
Thank you very much for your help. At some point soon I'll manage to partition the drive, and install ubuntu.

---

