---
title: "Firefox slow in Lucid:  Fixed"
date: 2010-05-01
forum: General Help
---

### Post by Don DeGregori on 2010-05-01
In Lucid Lynx (10.04), Firefox was slow to load web pages on my system. I fixed the problem by performing the option changes below. If Firefox on your system is normal, please disregard the changes. BE CAREFUL not to change the wrong option.  :)

Open your Firefox and type **about:config** at URL address bar and hit enter. To make a False into True, select the line to change, and double click. On the 2nd option change, right click and select Modify

- network.http.pipelining > Make it True
- network.http.pipelining.maxrequests > Make it 8 or 10
- network.http.proxy.pipelining > Make it True
- network.dns.disableIPv6 > Make it True

---

### Post by chessplayer on 2010-05-01
Thanks a lot for this post! This did it for me too!

Cheers,

chessplayer

---

### Post by winecurmudgeon on 2010-05-01
Did the trick. Thanks. I wasn't looking forward to trying to set Chrome up.

---

### Post by wojox on 2010-05-01
You can look here as well [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by lafcina on 2010-05-03
It is not working for me, new Firefox 3.6.3 is still slow on  Ubuntu 10.04.

It's interesting that when I changed parameters it workend fast until computer restart. Also I removed firefox-3.5-gnome-support (dummy upgrade package for firefox-3.5 -> firefox) and worked fast until restart.

Any ideas how to repair a problem ?
 
REgards

---

### Post by moodle on 2010-05-13
This solution didn't work for me either.  Why is Firefox so slow in Ubuntu compared to Windows?

---

### Post by wojox on 2010-05-13
You could always download Firefox from Mozilla, unpack it and mv it to /opt.

---

### Post by wkulecz on 2010-05-14
run this command in a terminal

date && nslookup msdn.com 8.8.4.4 && date

If its slow you have the same unsolved issue I have.  If its fast, messing around with firefox is probably the way to a solution.

---

### Post by Geos on 2010-05-15
Cheers Don DeGregori :)  This worked well for me.... cheers :cheers:

---

### Post by YuraYong on 2010-05-29
:KS:KS:P thank you! i just testing ubuntu with great interest...
going to dual boot ubuntu n windows7 :)
thank for above help to make firefox work like a charm!
now need to slowly figure out other thing about ubuntu!

---

### Post by finlost on 2010-05-29
FF might be set to IPv6

---

### Post by photodan on 2010-06-07
> **Don DeGregori said:**
> In Lucid Lynx (10.04), Firefox was slow to load web pages on my system. I fixed the problem by performing the option changes below. If Firefox on your system is normal, please disregard the changes. BE CAREFUL not to change the wrong option.  :)

Open your Firefox and type **about:config** at URL address bar and hit enter. To make a False into True, select the line to change, and double click. On the 2nd option change, right click and select Modify

- network.http.pipelining > Make it True
- network.http.pipelining.maxrequests > Make it 8 or 10
- network.http.proxy.pipelining > Make it True
- network.dns.disableIPv6 > Make it True

Thanks! Firefox is speedy again!   :)

Now I can stop using this weird-looking Chromium browser.

arkiedan

---

### Post by Danimoth on 2010-06-13
Tried everything, including IPv6 but no luck. The thing that did the trick for me was:
Edit->preferences->advanced, click on settings.
The default is "Use system proxy settings".
Select: "No proxy".

Enjoy :).

---

### Post by marvselby on 2010-06-14
I found that disabling the iTunes Application Detector in the add-ons solved my problem of very slow connection to websites.

---

### Post by zman50 on 2010-08-05
Don....YOU are the MAN! Was very unhappy with firefox on lucid compared to xp...After following your directions...NO problems....finds server fast and loads fast...THANKS!!

---

### Post by sydbat on 2010-08-05
Nice. Now pages load even BEFORE I click on them!!:p

---

### Post by rbock on 2010-08-11
Thanks a lot!:KS Firefox was so absurdly slow in resolving addresses. 

Turning off ipv6 was the essential option. Now I can really enjoy Lucid!

:popcorn:

---

