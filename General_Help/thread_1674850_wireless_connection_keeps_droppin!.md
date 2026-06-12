---
title: "wireless connection keeps droppin!"
date: 2011-01-24
forum: General Help
---

### Post by ninjaprawn on 2011-01-24
hi,

just installed kubuntu 10.10 on a dual boot with winxp on my asus r101 netbook. 
wireless connects perfectly, but after roughly 30 seconds, i cant access any address or ping an url or ip. however network manager says im still connected. so i click on network manager, and click on the wireless connection, it then reconnects in a couple of seconds, and all is good again. i carry on browsing, and 30 seconds later the same happens again!!!
my wireless signal is fairly week, however connection works everytime and in xp this is not an issue

any ideas? thanks :)

---

### Post by hwttdz on 2011-01-24
I had similar behavior.  If you're in a very high traffic area (i.e. you can see many wireless networks) then you might want to try disabling adaptive channel expansion on the router.  The issue I was having was that the router was changing channels so quickly that the computer wouldn't keep up.  This is a workaround, and there should be some method to change the interval for checking the current channel of the network, of course this workaround probably ends up working better in high traffic areas.

---

### Post by ninjaprawn on 2011-01-24
unfortunately i dont have physical access to the router :( so cant do that. im surprised tho cos in winxp, this is not an issue!
also, it is not a high traffic area either, there is only 2 other networks visible.
i forgot to mention, i am also running an archlinux box that has no issues with the same network, but am using wicd to manage that connection.

---

### Post by ninjaprawn on 2011-01-24
forget it, gonna put arch on the netbook instead now, cant be bothered waiting for no one to get back to me! :)

---

### Post by ninjaprawn on 2011-01-26
ok, so put archbang on instead, and the issue seems to have disappeared :) also, if anyone else has the same hardware, archbang seems to be able to do multitouch properly on the touchpad :)

---

