---
title: "Can't send email or post to boards"
date: 2010-05-07
forum: General Help
---

### Post by Solinoure on 2010-05-07
I'm posting this from my Vista Laptop.
I recently upgraded to Lynx and I can't access my Gmail account via the web. I can download emails with thunderbird, but I can't send emails.
I can log into chat boards and read posts but I can't make posts of my own.
Basically, Ubuntu won't let me push data out to the internet.

When I tried to post to this board from my Ubuntu box, it ends up where to save the file newthread.php.

Help!

---

### Post by finlost on 2010-05-07
Are you behind a firewall?

---

### Post by Solinoure on 2010-05-07
Yes - I suppose.
My internet is shared from an XP machine (with ICS) that has a 3G Wireless USB adapter.
The XP box has a firewall. I hadn't thought to mess with that as it lets my other machines manage with no tampering. I'll go fuss with it some and see what happens.

....

ok... I turned off the firewall on the machine that shares out the internet and I still have the same problem.

---

### Post by Solinoure on 2010-05-08
It would seem that part of the problem is firefox as I can post to boards with chromium. Still can't login to gmail or youtube.

---

### Post by Good_Newz on 2010-05-08
I have exactly the same problem. Mine started 2 days ago. I am not sure but could it be caused by an update?

---

### Post by Good_Newz on 2010-05-08
I can confirm the problem on another linux system (9.10). It seems the problem starts with upgrade of libsoup. Downgrade doesnt help.

---

### Post by Solinoure on 2010-05-08
I fixed it!
It turns out the issue was in the XP box sharing the internet connection.
Until recently, the only way to get it to share was to have windows control the local network while the adapter software managed the adapter.
I rebooted the XP box and let the adapter software handle it all and this worked!
I guess the folks at sprint finally got their software right... they have sent many updates for it of late.
Anyway, I now have full internet access from all of my machines.
Thanks a ton every one. I hope this solution works for you Good_Newz.

-Solinoure

---

### Post by Good_Newz on 2010-05-08
Ok, I solved my cannt login to gmail problem. Restart YOUR router. I have netgear. It started causing all kinds of weird problems(most on linux, no problems on windows) in the past couple of days. So unplug it from the power source then wait 10s and plug it in again. Hope this helps.

---

