---
title: "Grub configuration problem"
date: 2009-07-25
forum: General Help
---

### Post by platinum.zeppelin on 2009-07-25
First of all I know this problem is long solved where I have seen similar threads on this forum as well as others, except that none of the solutions provided worked for me..

I have just made the switch from Windows XP to ubuntu 9.04 (jaunty), but decided to keep the windows XP operating system, In addition to these two operating systems I als installed the latest kubuntu distribution. In either to make my mind wether KDE or GNOME.

Since kubuntu was the latest I installed, it became the default operating system. I tried to remove it by deleting its partition using gparted in ubuntu._**HERE comes the problem**_ when i rebooted the computer I got " Grub eroor 22" and none of the other operating systems would work..

eventually I had to reinstall kubuntu in the same partition it once occupied and its taking the most space while I dont use at all.

I tried all the steps in these links : 

[https://lists.ubuntu.com/archives/ubuntu-users/2006-October/095908.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-October/095908.html) 

[http://ubuntuforums.org/archive/index.php/t-126528.html](http://ubuntuforums.org/archive/index.php/t-126528.html)

[http://linux.about.com/od/ubuntu_doc/a/ubudg28t6.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg28t6.htm) 

I opened the grub menu list and changed " default 0 " to " default 1 " - " default 5 " each time saving the file... somehow no changes take place.

Any help would be greatly appreciated.

Thank you in advance

---

### Post by SuperSonic4 on 2009-07-25
Yeah, you removed grub because it resided on /boot in your kubuntu partition

I'm not aware of the problem nor the solution you want

---

### Post by platinum.zeppelin on 2009-07-25
I forgot to mention that I plan to make ubuntu my default then I think ( please telle me if this is correct) that i then will be able to format the kubunt partition.

---

### Post by SuperSonic4 on 2009-07-25
Yes, if you put grub onto your ubuntu partition then you will be able to reformat the kubuntu partition. Beware that if you install grub via another distro again the cycle will repeat itself. You could also make a dedicated /boot partition independent of an OS.

I believe you can install grub via the supergrubdisk which is on google

---

### Post by platinum.zeppelin on 2009-07-25
SuperSonic4 thank you for taking a look at the thread....

The problems are 2: 

1) I was not able to set ubuntu as my default operating system on boot.
2) I was not able to successfully remove kubuntu.

The main solution I am willing to get is how to remove the kubuntu operating system without having to reinstall ubuntu or windows xp.

---

### Post by platinum.zeppelin on 2009-07-25
Thank you very much SuperSonic4 I was able to download auto supergrub and it did the work just fine.

---

### Post by kdetech on 2009-07-25
You might not want to give up on Kubuntu. Its more user friendly and aesthetic and really keeps getting new features with updates.

---

### Post by SuperSonic4 on 2009-07-25
Kubuntu, although improving, remains a relative poor showing of what KDE can actually do. It would be unfair on KDE to judge based on kubuntu. Fedora, OpenSUSE, Mandriva and [arch +] KDEmod (available as a live cd via chakra) are considered to be the best KDE distros

Glad you solved your problem though ^-^

---

