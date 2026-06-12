---
title: "Ubuntu 9.10  - Internet does not work"
date: 2010-04-18
forum: General Help
---

### Post by Miltage on 2010-04-18
Hello,

Last night I switched from Windows XP to Ubuntu. This morning I could connect to my wireless network, but not access the internet. I tried several things like manually setting my IP address, but nothing seemed to work, then I found a solution on another site:

```
sudo dhclient wlan0
```After I performed that action, I could access the internet.
I then spent an hour and a half downloading and installing updates, before being prompted to reboot my laptop. I did so, but then could not access the internet again.

I have now spent my entire afternoon browsing the internet (on another computer), trying to find a solution. I tried that command again, which now does not work. I have also tried different DNS settings and even plugged an ethernet cable into my laptop, but the internet still doesn't work.

This is very frustrating, does anyone know how to fix this?

---

### Post by Iowan on 2010-04-18
Can you still connect to your wireless network? Check **ifconfig -a** to see if interface has an IP address.

---

### Post by Miltage on 2010-04-18
> **Iowan said:**
> Can you still connect to your wireless network? Check **ifconfig -a** to see if interface has an IP address.
Yes, it is connected.

---

### Post by Miltage on 2010-04-19
Nevermind, I seem to have fixed my problem. I have included my solution for anyone else who is experiencing similar problems.
 
Here is what I did:
 
Step 1: Format Hard Drive
Step 2: Install Windows 7
 
Internet is now working wonderfully. Thanks Microsoft!

---

### Post by Iowan on 2010-04-19
OK...
Guess we'll call this one [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

