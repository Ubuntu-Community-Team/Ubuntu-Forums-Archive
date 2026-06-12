---
title: "CPU fan on full blast"
date: 2009-07-02
forum: General Help
---

### Post by inTrouble on 2009-07-02
Maybe somebody came across this already and can help me out. Shortly after I boot up my cpu fan starts to rev up. Right now it's running at about 4600 rpm at only 23C. It is very annoying. This is not a Ubuntu problem since I get the same symptom on Winblows. Any ideas?
Thanks.

---

### Post by Noobs*McGee on 2009-07-02
I don't have any solutions (sorry, I'm a n00b) but I was wondering if you were using a program to view the performance of your hardware (i.e. fan speed and CPU temp.)?  I used to have a program for that when I was running WinXP, and I've been trying to find something similar since I switched over to Ubuntu, but so far I haven't had any luck.  I don't mean to hijack your thread or anything, just curious...

---

### Post by t4thfavor on 2009-07-02
I guess be thankful its on at all, mine never came on (until a recent update). Overheating == Very ANNOYING!

Sorry, no other help.

---

### Post by scrooge_74 on 2009-07-02
You need to describe more your PC so people can point you to the right solution, there are several ones depending on your hardware.

Some CPUs have frecuency scalling so the kernel gets to manage the fan depending on the work load, others don't (like my nx6110), so you have to do some work arounds to get it to do it

---

### Post by inTrouble on 2009-07-02
> **Noobs*McGee said:**
> I don't have any solutions (sorry, I'm a n00b) but I was wondering if you were using a program to view the performance of your hardware (i.e. fan speed and CPU temp.)?  I used to have a program for that when I was running WinXP, and I've been trying to find something similar since I switched over to Ubuntu, but so far I haven't had any luck.  I don't mean to hijack your thread or anything, just curious...

I  was using a widged in an earlier version but I don't remember what it was. Check the screenlets. I got the info now about the temp when I booted up.

---

### Post by inTrouble on 2009-07-02
> **scrooge_74 said:**
> You need to describe more your PC so people can point you to the right solution, there are several ones depending on your hardware.

Some CPUs have frecuency scalling so the kernel gets to manage the fan depending on the work load, others don't (like my nx6110), so you have to do some work arounds to get it to do it

Sorry, you're absolutely right.:oops:
So, I'm running Ubuntu 9.04 and Win Xp dual boot on an Intel P4 3.0 GHz processor w/3 Gig of Ram on a Biostar G31GVI mobo. I have 3 fans connected to this unit and when I first set it up, it was doing just fine. Any ideas?

---

### Post by Noobs*McGee on 2009-07-03
> **inTrouble said:**
> Check the screenlets.

Thanks, will do :)

---

### Post by scrooge_74 on 2009-07-03
You are going to have to look around for frecuency scalling for your version, there are instructions here in the forum.

But it could be as simple as adding to the bar the CPU frecuency icon, if yours has scalling it will let you manage your cpu right there. For me It would only run at full blast, then after some installing it will let me manage it.

good luck

---

### Post by PRC09 on 2009-07-03
Check in the bios for the motherboard.Sometimes the fan settings are controlled from there.If you have reset the bios to default values at any time then it may have turned the cooling fans to max.I know I have one system that is a biostar and you can vary the cpu fan speed setting.I just dont remember which heading it was under.

---

### Post by biglog on 2009-07-03
I had similar problem - only thing that worked for me was :

modified /etc/fancontrol

increased MINTEMP & MAXTEMP - runs at about 2800 rpm at rest now which is OK, was at 4500 all the time

---

### Post by XCan on 2009-07-03
I take it that you have checked whether or not you have any weird process eating 100% CPU all the time? I would think most CPU fans are controlled by the mobo receiving temperature either directly from the CPU or indicrectly by measuring it by itself (old AMDs).

---

### Post by inTrouble on 2009-07-03
Thanks everybody for their input. PRC09 was right about a setting in the system bios. I didn't know that I had that option (called smart fan). Again, thank you.

---

