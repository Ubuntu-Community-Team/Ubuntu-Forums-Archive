---
title: "Skype and teamviewer will not start on Ubuntu 11.10"
date: 2012-06-04
forum: General Help
---

### Post by unitedanarchy on 2012-06-04
Skype and teamviewer won't start for me, At all! I will search skype, And click on it, and it does nothing, It doesn't even close the dash board! I tried the portable version of teamviewer and the same thing happened. I always have problems with Ubuntu, It is so weird, I have always gotten problems. I don't know why it doesn't just work right, I know there is a reason for my problems, But I don't get why I keep getting these things that cause them in the first place though. I always get problems, But they are almost always different. Right now I have two other partitions that can't even connect to the internet for some reason, I'll probably make another post after I go into them and look around to see if I can fix it. Also, I can't share my internet connection through ethernet anymore. I don't know why, But when ever I go into connection info and tell it to share to other computers in ipv4 and restart it disconnects and reconnects constantly to the internet.

---

### Post by shafi.dude99 on 2012-06-04
> **unitedanarchy said:**
> Skype and teamviewer won't start for me, At all! I will search skype, And click on it, and it does nothing, It doesn't even close the dash board! I tried the portable version of teamviewer and the same thing happened. I always have problems with Ubuntu, It is so weird, I have always gotten problems. I don't know why it doesn't just work right, I know there is a reason for my problems, But I don't get why I keep getting these things that cause them in the first place though. I always get problems, But they are almost always different. Right now I have two other partitions that can't even connect to the internet for some reason, I'll probably make another post after I go into them and look around to see if I can fix it. Also, I can't share my internet connection through ethernet anymore. I don't know why, But when ever I go into connection info and tell it to share to other computers in ipv4 and restart it disconnects and reconnects constantly to the internet.


open skype from terminal and if there is any problem u paste it here

---

### Post by unitedanarchy on 2012-06-04
valeskagrim@ValeskaGrim:~$ skype
bash: /usr/bin/skype: No such file or directory
valeskagrim@ValeskaGrim:~$ start skype
start: Unknown job: skype
valeskagrim@ValeskaGrim:~$ sudo apt-get install skype
[sudo] password for valeskagrim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
valeskagrim@ValeskaGrim:~$ 

I did the last one to show I have it installed.

---

### Post by shafi.dude99 on 2012-06-04
> **unitedanarchy said:**
> valeskagrim@ValeskaGrim:~$ skype
bash: /usr/bin/skype: No such file or directory
valeskagrim@ValeskaGrim:~$ start skype
start: Unknown job: skype
valeskagrim@ValeskaGrim:~$ sudo apt-get install skype
[sudo] password for valeskagrim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
valeskagrim@ValeskaGrim:~$ 

I did the last one to show I have it installed.

can u show the output of 
whereis skype

---

### Post by unitedanarchy on 2012-06-04
valeskagrim@ValeskaGrim:~$ whereis skype
skype: /usr/bin/skype /usr/share/skype
valeskagrim@ValeskaGrim:~$

---

### Post by mike555 on 2012-06-04
I have found it necessary to delete the hidden file " .teamviewer " between uses .then it works good using the portable version 6 .


  If teamviewer portable has never started for you , make sure it is executable in properties.

---

### Post by unitedanarchy on 2012-06-04
I tried apt-get purge of skype and removing the .skype folder, But when I reinstalled skype it still did the exact same thing. And teamviewer still didn't work, And I couldn't find a portable version of teamviewer6, I still haven't tried the portable of teamviewer7 though. I really just want these things fixed so I can get them installed.

---

### Post by mike555 on 2012-06-04
[http://www.portablelinuxapps.org/network/teamviewer](http://www.portablelinuxapps.org/network/teamviewer)

[http://www.portablelinuxapps.org/network/skype](http://www.portablelinuxapps.org/network/skype)

---

