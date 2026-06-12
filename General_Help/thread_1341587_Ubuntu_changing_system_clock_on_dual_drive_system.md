---
title: "Ubuntu changing system clock on dual drive system"
date: 2009-11-29
forum: General Help
---

### Post by AndrewGen on 2009-11-29
I've been using Ubuntu 9.10 for several days now and I like what I see so far. One problem that I'm experiencing is that Ubuntu is changing the system time on my dual drive system. I have Windows 7 on one physical drive, and Ubuntu 9.10 on the other. Everytime I boot into the Ubuntu drive, and then boot into the Windows drive, the system clock has been changed by several hours. Has anyone else experienced this, and is there a fix?
 
Thanks,
Andrew

---

### Post by john newbuntu on 2009-11-29
Lookup this thread for a possible solution:
[http://ubuntuforums.org/archive/index.php/t-836480.html](http://ubuntuforums.org/archive/index.php/t-836480.html)

---

### Post by AndrewGen on 2009-11-30
[FONT=Verdana]I GOT IT !!![/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]I was unable to change the UTC time using /etc/default/rcS in terminal mode due to permission issues, but I searched the forum and then tried gksu gedit /etc/default/rcS.... IT WORKED.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]This stuff is cool.  I&#8217;m learning.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]Thanks everyone.[/FONT]

---

### Post by Locutus_of_Borg on 2009-11-30
windows uses local time to set the clock

are you using utc in linux?

if so change to local time and that ought resolve the problem

---

### Post by AndrewGen on 2009-11-30
[FONT=Verdana]I was unable to change the UTC time using /etc/default/rcS in terminal mode.due to permission issues, but I searched the forum and then tried gksu gedit /etc/default/rcS IT WORKED.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]This stuff is cool.  I’m learning.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]Thanks everyone.[/FONT]

---

### Post by Locutus_of_Borg on 2009-11-30
sudo dpkg-reconfigure tzdata

---

