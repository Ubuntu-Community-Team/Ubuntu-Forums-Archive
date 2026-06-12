---
title: "Ubuntu won't boot"
date: 2010-09-21
forum: General Help
---

### Post by Urhungry on 2010-09-21
I installed slim to see what it was like, and I set it as the default desktop manager. Now when I try to boot up it keeps playing the startup animation forever. If I press escape to view what command is running it simply says starting slim, but never does. How can I change back to gdm? Thanks.

---

### Post by Urhungry on 2010-09-22
Anyone? I can't use my computer at all until this is fixed. If I could just get inti a terminal I could fix it from there.

---

### Post by 23dornot23d on 2010-09-22
Can't you boot up in safe mode ..... do you get to a boot menu at all ?

---

### Post by SmokeyThePanda on 2010-09-22
If you can get into a terminal on the system, install gdm and run:
```
sudo dpkg-reconfigure gdm
```

---

### Post by SmokeyThePanda on 2010-09-22
Just read your second post..Hmm. O.o I'm not sure if you can't get into a terminal.

---

### Post by Urhungry on 2010-09-22
If I boot into safe mode from grub it appears to work, but pushing the arrow keys just daisplays the ubuntu start up logo, and nothing else does anything.

---

### Post by SmokeyThePanda on 2010-09-22
Hmm..I'm not sure :( Perhaps someone will come along with a good solution. Just give it a day or so. :) You can easily use a live cd until then, if you absolutely need the computer. I've done it a few times while downloading isos, back when I only had one CD-RW xD

---

### Post by 23dornot23d on 2010-09-22
Ctrl + Alt + F1 ...... in safe mode ..... what does that do ?

if you do manage to get to a terminal ..... 

do

sudo aptitude update
sudo aptitude install gdm

startx or reboot ....

---

### Post by mahesh_p on 2010-09-22
its been 2-3 weeks since i ve installed ubuntu 10.4..i also have windows 7...its pirated and i also installed a windows activator patch...for 2 weeks it worked fine..but suddenly none of them are booting..i get the grub window to choose the os to boot..but after selecting win7 or ubuntu..the screen freezes...i ve tried almost everything possible..the win 7 cd is not booting..first it showed the startup repair msg..and wen i ran startup repair..it completed..and the error msg showed that it has a patch installed which is not letting boot windows..its been 5 days i am not able to use my comp..its a gateway laptop..plz help me!!!!and also wen i select ubuntu in grub it shows a blinking cursor..and doesnt move ahead..it freezes there itself....and wen i select windows it freezes on the windows logo......HELP ME!!!!

---

### Post by Urhungry on 2010-09-22
Ok, thanks. I didn't try ctrl-alt-f1 in safe mode, guess it didn't occur to me. I'll try it when I can in about 13 hours :)

---

### Post by Urhungry on 2010-09-22
> **mahesh_p said:**
> its been 2-3 weeks since i ve installed ubuntu 10.4..i also have windows 7...its pirated and i also installed a windows activator patch...for 2 weeks it worked fine..but suddenly none of them are booting..i get the grub window to choose the os to boot..but after selecting win7 or ubuntu..the screen freezes...i ve tried almost everything possible..the win 7 cd is not booting..first it showed the startup repair msg..and wen i ran startup repair..it completed..and the error msg showed that it has a patch installed which is not letting boot windows..its been 5 days i am not able to use my comp..its a gateway laptop..plz help me!!!!and also wen i select ubuntu in grub it shows a blinking cursor..and doesnt move ahead..it freezes there itself....and wen i select windows it freezes on the windows logo......HELP ME!!!!

Shouldn't you make your own thread? Anyway, when I get grub problems I just reinstall, but you probably don't want to do that. I can't help of it's a problem with the pirated windows deal.

---

