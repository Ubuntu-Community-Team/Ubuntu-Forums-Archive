---
title: "system slowly freezes then appears to shutdown"
date: 2012-07-07
forum: General Help
---

### Post by mrchumpley on 2012-07-07
as of 48 hours ago shortly after booting up and logging in the screen slowly freezes then locks. a little while later it goes blank and the monitor shows no analogue input, as though it's hibernating. sometimes it freezes at the login page, before anyone has logged in. Sometimes it freezes but the mouse still moves about on the screen but the screen itself is locked along with the keyboard.

it is not a processor temperature problem, and the systems runs fine from a live CD so again that rules out a hardware issue.

I've tried booting to an older version but get a screen telling me 

mountall: Disconnected from Plymouth

Ubuntu 10.04.4 LTS Ubuntu1 tty1

Ubuntu1 login:~$

I'm sure this is some software glitch triggered by a recent update for Lucid Lynx 10.04. Can anyone suggest anything?

Many thanks

mrc

---

### Post by msammels on 2012-07-07
Perhaps it's a CPU issue. Have you tried:

```
sudo top
```

To find out if one of the processes is using an amazing amount of CPU?

---

### Post by mrchumpley on 2012-07-07
Just checked: no, nothing much going on. CPU use below 20%. then suddenly locked again whilst I was watching.

---

### Post by msammels on 2012-07-07
OK, this is a bit silly, but have you opened your machine and gone "phewhewehwew" and cleaned out all the dust? Sometimes if the fan gets clogged, overheating can occur.

---

### Post by mrchumpley on 2012-07-07
I did do that.

Also - I have checked the processor temperatures and they're around 40 centigrade so don't think it's that.

---

### Post by msammels on 2012-07-07
Ah yes, but overheating of the hard drives can cause the same thing. Same with the RAM. OK, so here's an idea: backup or move /home to a new partition and reinstall 10.04. Watch the system for a while. If it freezes, we still have a problem.

---

### Post by mrchumpley on 2012-07-07
how do I move the home directory to another partition?

I have an empty partition called "Documents" where I could move it to.

Thanks
mrc

---

### Post by msammels on 2012-07-07
Ah, in that case it could be easier just to copy/paste stuff from home, if there's enough space. It all depends how many partitions your hard drive(s) has/have.

---

### Post by mrchumpley on 2012-07-07
Okay I'll try that - although the system rarely runs for long enough to allow me to move stuff.

---

### Post by msammels on 2012-07-07
If you have big trouble, move it in small bunches. Here's a question though: if you let the system idle, does it still go "hurk, BLEH!"?

---

### Post by mrchumpley on 2012-07-08
I have now installed 12.04 to a fresh partition and the same thing is happening: it boots up fine, then after a minute or so the mouse starts to get jumpy (moving and stopping intermittently) and none of the mouse buttons or keyboard buttons work.

As I said before - this is very odd given that everything works fine when booted from CD so seems to rule out a hardware problem. An now I am running a brand new operating system on a freshly partitioned section of the hard drive! 

I just don't get it...

---

### Post by gync2 on 2012-07-08
Çàõîäè è çàðóæàé ëþáûé ôàéëû - ôîòî, âèäåî, ìóçûêó, èãðû, äîêóìåíòû. Áûñòðûå ñåðâåðà. Íåîãðàíè÷åííîå äèñêîâîå ïðîñòðàíñòâî.  Çåðêàëà: [http://walkgraphislihardno.land.ruhttp://prosislinwea314.fromru.suhttp://ohgenhamisupptweak.land.ruhttp://anastiyakha899a.hotmail.ruhttp://ballsatpcalwalenma.nightmail.ruhttp://afagisec776.fromru.suhttp://ratanarumreapa.pop3.ruhttp://mudromicsa588.fromru.suhttp://diastanmosgaiproddie.hotbox.ruhttp://dzhambulatshi.pochta.ru](http://walkgraphislihardno.land.ruhttp://prosislinwea314.fromru.suhttp://ohgenhamisupptweak.land.ruhttp://anastiyakha899a.hotmail.ruhttp://ballsatpcalwalenma.nightmail.ruhttp://afagisec776.fromru.suhttp://ratanarumreapa.pop3.ruhttp://mudromicsa588.fromru.suhttp://diastanmosgaiproddie.hotbox.ruhttp://dzhambulatshi.pochta.ru)

---

