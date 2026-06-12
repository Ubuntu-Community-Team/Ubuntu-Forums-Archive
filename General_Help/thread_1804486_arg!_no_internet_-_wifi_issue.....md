---
title: "arg! no internet - wifi issue...."
date: 2011-07-14
forum: General Help
---

### Post by F.G. on 2011-07-14
hi,
so i saw a similar post a while ago, though can't seem to find it again.  basically my wireless internet register's as being connected, though when I try to connect, web pages procrastinate and nothing happens 'till i get an error message.  now i've been using two wireless cards and two access points (my neighbor and i are on good terms), the two wirelss cards are an rtl8187 and a rtl8187b (one external and one internal).

it looks connected, sometimes it works, otherwise it spends ages and i just get an error. when i get this it stays this way for a while.

i remember having a similar issue with jaunty (i think it was jaunty, it was a couple of years ago) and the sollution was to add something like adding: 
```
iwconfig set rate 5M wlan0 //or whatever wireless interface
``` to the end of a file called something like /etc/rclocal.

i have no idea why this worked, or if this is the same problem.

i tried using windows xp and only one of my wireless cards was supported also only the closer AP was picked up, so i really don't know where the problem is.  

unfortunately i don;t now have easy internet access, so researching this is a nightmare.
any help will be very welcome.

ps. i hope this post works!!

---

