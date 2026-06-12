---
title: "Newbie cant get crontab to work"
date: 2010-01-10
forum: General Help
---

### Post by Nathan_84 on 2010-01-10
Hi all, 

Ok let me first start by introducing myself. I'm completely new to Linux. I've always argued Windows was better, even if I secretly thought not. Anyways the time has come to make the transition (i'm moving into computer forensics so I need to learn linux :) )

SO i'm trying to use crontab -e. I've installed gnome scheduler as i'm not comfortable editing in command line yet. 

I've setup blackjack to start everyday at 23.30. The command line i've entered is /usr/games/blackjack and this works perfectly fine in command line.

I've been trying for 3hours :( IT JUST WONT WORK!!! ARJHHH

Please please can someone help

Thanks and I apologise for babbling on

---

### Post by dcstar on 2010-01-11
> **Nathan_84 said:**
> 
..........
SO i'm trying to use crontab -e. I've installed gnome scheduler as i'm not comfortable editing in command line yet. 

I've setup blackjack to start everyday at 23.30. The command line i've entered is /usr/games/blackjack and this works perfectly fine in command line.

I've been trying for 3hours :( IT JUST WONT WORK!!! ARJHHH
..........

That's right, any GUI app has no idea whatsoever to send the screen output when run by a scheduler - do a forum search for a detailed solution.

---

### Post by kpkeerthi on 2010-01-11
**_Hint:_** You need DISPLAY variable in your command

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

