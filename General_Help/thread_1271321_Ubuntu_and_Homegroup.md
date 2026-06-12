---
title: "Ubuntu and Homegroup"
date: 2009-09-20
forum: General Help
---

### Post by TarasIv on 2009-09-20
Hey, I am wondering if there is anyway I can connect to my Windows 7 machine and use its printer? This would save me a lot of time! Thanks in advance! Sorry, if I'm nooby, but I just installed Ubuntu yesterday, but I really like it so far!

---

### Post by TarasIv on 2009-09-20
Can someone please help? Sorry if I seem needy, but, I am actually. ;)

---

### Post by TarasIv on 2009-09-20
Is anyone going to help me?

---

### Post by TarasIv on 2009-09-20
*bump*
I feel like such a jerk when I keep bumping my thread, so sorry. But I really need help.

---

### Post by TarasIv on 2009-09-20
*bump*

---

### Post by louieb on 2009-09-20
Is your printer set up for sharing in win 7? 

In Ubuntu System>Administration>Printer.

Btw we all volunteer time here. Its ok to bump but only once a day.

---

### Post by TarasIv on 2009-09-21
Awesome, thank you, and I won't bump my threads anymore :D

---

### Post by billcondie on 2009-12-06
I can see my Windows7 PC under Places>Network.It says I'm in Workgroup

But it won't accept my Windows-generated Homegroup password and I can't even call up my Public folders.

Help!

(I promise not to Bump)

---

### Post by audiomick on 2009-12-06
Hi Bill.
Bumping is ok, as long as it isn't every 5 minutes...;)

This is a huge read:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

but dmizer seems to be the god of samba shares. Have a look through it, and maybe stick a post in there.
Michael

---

### Post by billcondie on 2009-12-06
Great link, thanks. STILL muddling around with it :-)

One quick question:

When I click Network and click on my Windows machine, I see my Ubuntu username

Is the password at this point my Ubuntu password or my Windows Homgroup password? (neither is working. Yet . . .)

---

### Post by audiomick on 2009-12-06
The password you need is the one for windows. Make sure the workgroup name is right too.

---

### Post by zach.detton on 2010-03-27
Ubuntu currently cannot see files of folders shared via the Home Group feature in Windows 7. This is because Samba was designed to speak with the CIFS protocol that Windows has used for Network Sharing for years, however, Microsoft developed a new protocol for the Home Group feature.

Using Samba you can access network shares you have to manually enable in Windows but you will not be able to access anything shared by Home Group. You can read up all about it [here]("http://74.125.95.132/search?q=cache:cqNk8vlDqu8J:download.microsoft.com/download/a/e/6/ae6e4142-aa58-45c6-8dcf-a657e5900cd3/%255BMS-HGRP%255D.pdf+what+protocol+is+used+for+Windows+homegroup%3F&cd=2&hl=en&ct=clnk&gl=us")

---

### Post by Mark Phelps on 2010-03-27
Don't feel bad, XP and Vista machines can't use the HomeGroup features, either.

---

### Post by pwm5js on 2012-03-19
Hi All,
Does anyone know if this issue with Ubuntu communicating with Windows 7 Homegroup has been resolved?

Thanks
Pete

---

