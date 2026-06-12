---
title: "$PATH in /etc/environment don`t effect in xfce-terminal"
date: 2012-06-26
forum: General Help
---

### Post by h113331pp on 2012-06-26
Hi all:
   When I enter the Xfce desktop, I clicked right mouse button and choose the termianl, I enter "echo $PATH", and get return below":
/usr/local/bin:/usr/bin:/bin:/usr/games

and my /etc/environment is:
PATH="/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/sbin:/usr/local/bin:/opt/jre/bin"

and if I use ctrl + alt + F1 to switch to tty1, and enter "echo $PATH", I got:
/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/sbin:/usr/local/bin:/opt/jre/bin

looks like the xfce-terminal didn`t set my $PATH correctly, but I don`t know how to solve it.

Could some one tell me how to solve this weird problem?

p.s: 
    I also edit /etc/gdm/gdm.conf, no effect.
    but when I use "startx" instead "sudo service gdm start", my $PATH will be correct.

---

### Post by h113331pp on 2012-06-27
Ok, it seems a gdm bug, I install lightdm and don`t have the bug anymore, but if I use gdm or slim instead, the problem will appear.

by the way, how do I change the login manager? when I install gdm, ubuntu 12.04 pop up a purple console, and ask me which manager to use, how do I wake this this purple console again?

---

### Post by h113331pp on 2012-06-27
people in launchpad give me a answer, I think it`s useful:
[https://answers.launchpad.net/ubuntu/+source/gdm/+question/201680](https://answers.launchpad.net/ubuntu/+source/gdm/+question/201680)

so edit the /etc/bash.bashrc could solve the problem.

---

