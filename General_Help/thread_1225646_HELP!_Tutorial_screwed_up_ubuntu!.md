---
title: "HELP! Tutorial screwed up ubuntu!"
date: 2009-07-28
forum: General Help
---

### Post by Theory5 on 2009-07-28
I was following the tutorial here [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012) to try and get ubuntu to recognize the other stuff such as right clicking with the stylus, and rotating the screen. But now ubuntu refuses to boot. It starts up and then after taking a long time to boot it goes to a black screen with bits of orangish red at the top! Could somebody help me revert my installation back to the way it was? and it added another entry in GRUB. its the same entry as the other ubuntu one. and I just ran recovery mode but all that did was make it so blue and green lines are displayed alongside the redish ones.It also said something about the xorg conf file being modified.

---

### Post by Theory5 on 2009-07-29
*annoyed bump*

---

### Post by wojox on 2009-07-29
So you can't even get into a terminal and copy your xorg.conf.backup to xorg.conf?

What about your install cd?

---

### Post by Theory5 on 2009-07-29
> **wojox said:**
> So you can't even get into a terminal and copy your xorg.conf.backup to xorg.conf?

What about your install cd?

oh, lol I hadnt even thought of that. Im kinda new to ubuntu. I guess I can do that in recovery mode. What are the path names?

---

### Post by nikhilk on 2009-07-29
> **Theory5 said:**
> What are the path names?

The absolute path is /etc/X11/xorg.conf

---

### Post by Theory5 on 2009-07-29
and how can I get rid of the two extra GRUB entrys?

---

### Post by jimmyhacker on 2009-07-29
try making ctrl+alt+F1

and login with your username and password

NOTE:you will not see your password or ****`s

after logging,type sudo dexconf

if it asks your password,type it.
press ENTER (it`s located between delete and " :)"
and reboot

if it works,ask mods to give me a bean :P

---

### Post by zarqoon on 2009-07-29
all grub entries are set in /boot/grub/menu.lst
You can remove the entries you do not need.
I suggest you make backup in case you remove something you need.

---

### Post by Theory5 on 2009-07-29
> **jimmyhacker said:**
> try making ctrl+alt+F1

and login with your username and password

NOTE:you will not see your password or ****`s

after logging,type sudo dexconf

if it asks your password,type it.
press ENTER (it`s located between delete and " :)"
and reboot

if it works,ask mods to give me a bean :P

yea, I tried to get into a virtual terminal, but it didnt work. It did work through recovery mode though.

---

### Post by TrakerJon on 2009-07-29
Just do a reinstall...or you'll be spending days getting it straight. This should help speed things up...

[http://ubuntuforums.org/showthread.php?t=1181327]("http://ubuntuforums.org/showthread.php?t=1181327")

---

### Post by Theory5 on 2009-07-29
how is that other thread supposed to help? And it was a B**** to get everything working right the first time I installed it. Im going to use the backup Xorg server file, then I will remove all traces of that program from my computer and run it correctly.

---

### Post by Theory5 on 2009-07-29
Taking a backup and reusing it as the xorg.conf file didnt work, so I am just reinstalling it.

---

