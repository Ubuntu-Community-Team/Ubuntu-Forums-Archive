---
title: "I can't boot in Kubuntu after power failure"
date: 2009-11-05
forum: General Help
---

### Post by quangtuan on 2009-11-05
I'm a newbie,i've just used kubuntu for a week.I installed Kubuntu 9.10 with Wubi.After a power cut,i started my computer,but there was only a black screen with this line:"sh:grub>"
What's the matter with kubuntu?How can I resolve my problem?Please,help me!

---

### Post by pskrzypol on 2009-11-05
try to run windows, close it properly and then run Kubuntu

---

### Post by quangtuan on 2009-11-05
Nothing different.There's still a black screen:mad:.

---

### Post by Muhammad Ahmed on 2009-11-05
may be the grub,try reinstalling the grub from live cd

---

### Post by quangtuan on 2009-11-05
I've tried with live cd but it didn't work.It couldn't find kubuntu on my harddisk.

---

### Post by ranch hand on 2009-11-05
I would recommend, to everyone, to consider investing in a UPS.  They save a lot of hard work and heart break.

I use an APC Smart-UPS.  Fully supported by Ubuntu (and Kubuntu) and MS.  Usb or serial cable connection.  Will, when its battery is low, shut the box down.  When the batery is back up it will restart to the point the box was at when it shut down.

Other UPS makers probably offer the same type of service.

---

### Post by quangtuan on 2009-11-06
> **ranch hand said:**
> I would recommend, to everyone, to consider investing in a UPS.  They save a lot of hard work and heart break.

I use an APC Smart-UPS.  Fully supported by Ubuntu (and Kubuntu) and MS.  Usb or serial cable connection.  Will, when its battery is low, shut the box down.  When the batery is back up it will restart to the point the box was at when it shut down.

Other UPS makers probably offer the same type of service.

Thanks for your advice!I will buy an UPS.
Is it impossible to make Kubuntu work?

---

### Post by ranch hand on 2009-11-06
I am sorry but I know nothing about wubi at all.  I will not have MS on my box so that is kind of out.

Have you booted to your LiveCD and had a look around with that?  It should see a lot more of  your drive than anything that you can do with MS.

I really am not a fan of VB or VM either.  I like to multi boot.  Do you have 30 to 50Gb available for that?  Just as a way out if you are hosed in your current setup.

---

### Post by quangtuan on 2009-11-07
I've reinstalled Ubuntu with CD,not through Wubi.And I feel it runs faster and more stable:p.
Anyway,thanks for your help!!!):P

---

### Post by Dr Droid on 2010-06-09
This solution is in other threads (thanks meierfra)... boot into windows open command prompt type 
```

chkdsk [drive letter the root.disk and swap.disk files are on] /F

```
 
and then shut down completely, USING THE START MENU.

---

