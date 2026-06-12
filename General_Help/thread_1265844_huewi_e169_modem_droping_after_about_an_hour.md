---
title: "huewi e169 modem droping after about an hour"
date: 2009-09-13
forum: General Help
---

### Post by dj-toonz on 2009-09-13
Hi all I've got a Huewi E169 modem & don't know what's going on with it at the moment, after about an hour it drops the connection :-( and doesn't re-connect (got it to connect automatically) ticked in the mobile broadband settings in NetworkManager Applet 0.7.0.100, this has been going on for the past week now :( in windows xp I can stay on as long as I want (till I press disconnect) but in jaunty it won't connect after it drops :( what's going on. has a kernel update broke it or something? the kernel that I'm using is 2.6.28-15-generic if that makes any sense. I'm using Three Uk & they said that theres no problem @ there end & if I can stay online for ages in windows it must be a problem with Linux :-( I've tried updating network Manager & it still drops the connection, & got the dns settings set to opendns. what's going on at the moment & anything I can do to fix it? cheers

---

### Post by dj-toonz on 2009-09-14
I'm getting sick of this now :( every 5 or 10 minutes it's dropping, to download anything I have to use windows, before last Saturday I could leave Ubuntu Jaunty up for days without the connection dropping & when it did, it used to auto re-connect but it ain't doing that now :( when it does disconnect it used to start spinning and then connect but now it's just saying 3 has disconnected and no longer connects. thinking of throwing this dongle in the bin if it carries on :(

---

### Post by P4man on 2009-09-14
perhaps you could try gnome-ppp. Have a look here:
[http://ubuntuforums.org/showthread.php?t=843973](http://ubuntuforums.org/showthread.php?t=843973)

Its meant for another modem, but should work for yours as well I think.

---

### Post by dj-toonz on 2009-09-14
Thx for that, Modem works ok under Jaunty, that's not the problem, the problem, Is for the past week or so, Connections been dropping like flies :( Before the past week, Jaunty was stable & network manager used to work proper, I could leave Jaunty up for hours or days without the connection dropping, but now doesn't stay up for more then an hour or more :(. looks like a kernel update or a software update what's killed it, but haven't a clue which one's causing the problem :(

---

### Post by P4man on 2009-09-14
IT could just be network manager that is crapping out (its not like thats unheard of :) )thats why I suggested trying ppp dialup.

---

### Post by dj-toonz on 2009-09-14
Thx for that advice but I've been trying to use ppp for ages but it doesn't seem to work with 3.5g dongles :( it doesn't seem to pick up the E169 dongle. it's every hour it's dropping as it was an hour from the last post in here & it's just bloody dropped again :( I thought the network manager re-connects after it's dropped connection, but it seems to not be doing. is there any cause to why that is?

---

### Post by dj-toonz on 2009-09-14
10 minutes that last even with using PPP :( don't know what's going on with PPP & Network Manager for the past week or so, It's doing me nut in, I get longer up time in windows then I'm doing in ubuntu at the moment :(. How can you do a test to see if it is a kernel or network problem? as if it is a bug in the kernel, I could report it & see if it is or not

---

### Post by t0p on 2009-09-14
I dunno if [this]("http://linuxgazette.net/165/misc/lg/erratically_dying_pppd.html") will help.  It doesn't specifically address your problem, but it *is* similar (gprs modem works in much the same way as an hsdpa modem).

---

