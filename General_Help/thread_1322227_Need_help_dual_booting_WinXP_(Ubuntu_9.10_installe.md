---
title: "Need help dual booting WinXP (Ubuntu 9.10 installed)"
date: 2009-11-10
forum: General Help
---

### Post by quake&gt;sex on 2009-11-10
Hello, 

Thanks in advance for everyone who has made linux what it is.

I am new to linux but am learning fast thanks to Ubuntu 9.10. 

My problem is this: I can't find a single tutorial that explains how to dual boot Windows XP onto a machine running Ubuntu 9.10.  They are all geared for older versions of Ubuntu and consequently older versions of GRUB. 

Because these tutorials refer to a file called "menu.lst", located in earlier versions of ubuntu in the /root/grub folder, on 9.10 it's impossible to follow the instructions since 9.10 has what is called GRUB2 and consequently the menu.lst file doesn't exist!

(it's replaced by grub.conf and looks different, sadly.)

Can somebody be so kind as to give a step by step instruction for how to dual boot windows xp onto an Ubuntu 9.10 machine? My lack of linux knowledge would make it difficult to only get a snippet of info - hence the reason I am asking for step-by-step instructions. 

Thank you, please respond! :)

p.s. I want to dual boot ONLY because I want to game hassle free. I hate Microsoft. Long live (and love) Linux.

---

### Post by dvlchd3 on 2009-11-10
Follow the other guides on how to create the space for Windows, install windows.  Then you will have to boot into the Ubuntu 9.10 live CD and follow the tutorial:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

which will describe how to recover GRUB 2 after a windows installation.

Hope this helps!

---

### Post by quake&gt;sex on 2009-11-10
Wow, talk about a speedy reply!

Thank you [dvlchd3]("http://ubuntuforums.org/member.php?u=295128"), I hope it helps too.

I will have a chance to check it out when I return from a short trip to the grocery store.

Thanks for the help ;)

---

### Post by krakenfury on 2009-11-10
Or you could back up your home folder and repartition.  Windows will fight and kick and scream to be on the first partition.  Grub 2 is very different, you modify your main config file by editing other files and running 'update grub'.  If you don't have a lot of Linux knowledge and you don't have a stable, tricked out, year old install, I recommend installing Windows first, then letting grub configure itself to accommodate it after you install Ubuntu.

---

