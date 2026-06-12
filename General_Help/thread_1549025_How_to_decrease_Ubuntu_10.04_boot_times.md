---
title: "How to decrease Ubuntu 10.04 boot times?"
date: 2010-08-09
forum: General Help
---

### Post by mahela007 on 2010-08-09
There seems to be quite a craze about reducing the Ubuntu boot times to 10 seconds. I never really reached the 10 second mark.. for me it was more like 30 seconds from when I selected Ubuntu in GRUB to when I was prompted to type in the password in GDM. 
First of all, is this what is meant by boot time? 
Secondly, I know this already is quite a good 'boot' time, but just for the sake of tinkering around, is it possible to reduce the time that elapses between the GRUB menu and GDM?

---

### Post by aeiah on 2010-08-09
boot time i usually considered the time from when grub starts to load the operating system to when you have a login prompt, or desktop, if auto-login is enabled.

there are many factors and it might not all be down to config. for instance, if you have several partitions, or indeed several hard drives then you will find that the boot time can take longer (as it has to initialise and check these partitions at boot).

but anyway, i guess your first port of call should be to disable any startup applications and services that you know you won't need (eg, bluetooth etc). note that even if you dont have a printer, you may still want cups to be enabled if you ever print to pdf files.

there are plenty of articles that go into more depth. a lot will suggest installing bootchart so you can get a chart of what processes are running at bootup and how long they take etc.

---

### Post by mahela007 on 2010-08-09
I have a dual boot system... maybe those extra partitions contributes to the moderately long boot times. I also have two hard drives.. Thanks for the advice. I'll give bootchart

---

### Post by dino99 on 2010-08-09
mostly due to plymouth: so either uninstall it or remove "splash" into /etc/default/grub, then update-grub again

---

### Post by trp on 2010-08-09
I have 10.04 on my Dell Mini 9 and from the time I log in to the desktop screen is less than 7 sec ( I timed it).  Can`t ask for much faster than that!  9.10 was much much slower, so the guys at Canonical deserve a well deserved job well done!  :D  P.S.  I also have a bios password as well.


Regards

---

### Post by mahela007 on 2010-08-10
> **dino99 said:**
> mostly due to plymouth: so either uninstall it or remove "splash" into /etc/default/grub, then update-grub again

What is plymouth? I've seen it mentioned here and there in Ubunu reviews. What does it do ?

---

### Post by garvinrick4 on 2010-08-10
Make a small partition and download netbook 10.04 release and install in partition and screw around with is fast on boot and fun to play with. Is worth having on machine for 
me anyway. It will surprise you.

[Netbook | Ubuntu]("http://www.ubuntu.com/netbook")

---

### Post by mahela007 on 2010-08-19
OK.. So I ran bootchart and here are the results. Can someone help me understand this and show me what I can do?

---

### Post by NCLI on 2010-08-19
> **mahela007 said:**
> OK.. So I ran bootchart and here are the results. Can someone help me understand this and show me what I can do?

Please upload it to a seperate site, then post a link here. Uploading it to the forum makes it unreadable :(

---

