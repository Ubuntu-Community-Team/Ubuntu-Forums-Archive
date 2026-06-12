---
title: "Why does the Traffic England website not work for me?"
date: 2011-05-04
forum: General Help
---

### Post by Man_Beach on 2011-05-04
If I click on any of the areas on the Traffic England website [http://www.trafficengland.com/](http://www.trafficengland.com/) a map comes up then there is a message 'wait for applet to be loaded, things are definitely being downloaded, then... nothing.

Do I need to install Sun Java or something? Currently I just have the default openjdk-6 installed.

---

### Post by oldos2er on 2011-05-04
Do you have Javascript enabled?

---

### Post by Man_Beach on 2011-05-04
IcedTea NPR Web Browser plugin

---

### Post by cpmman on 2011-05-04
Do you use noscript?

You need to allow 195.188.249.37 as well to get the detailed map.

---

### Post by Man_Beach on 2011-05-04
> **cpmman said:**
> Do you use noscript?

I've just googled noscript and it's turned off by default, so I suppose that I don't.

---

### Post by blueridgedog on 2011-05-04
Which browser?

---

### Post by Man_Beach on 2011-05-05
Firefox

---

### Post by Man_Beach on 2011-05-06
And if I click on the 'View Large Map' button I get a large map which I can't close and which breaks Firefox.

---

### Post by oldos2er on 2011-05-06
> **Man_Beach said:**
> IcedTea NPR Web Browser plugin

Java and javascript are two different things. If you're using Firefox, check Edit, Preferences, Content, and make sure the box configuring javascript is checked.

---

### Post by Man_Beach on 2011-05-08
It's checked. Does what I'm experiencing happen to anyone else? 
All I get is a blank area with "Wait for applet to be loaded..."?

---

### Post by coldraven on 2011-05-08
Using Firefox I get the same problem, it's a badly written web-site. They probably only expected Internet Explorer users!
I just tried it using Opera and it works OK.
I always have several browsers as you get this problem all over the net.
Chromium, Opera, Firefox and Midori are installed at the moment.

---

### Post by coffeecat on 2011-05-08
@Man_Beach, the site loaded just fine for me with Firefox 4 in Natty/11.04, and I was able to click on the M25 and M1 buttons and view the dynamic maps. But then Firefox suddenly crashed. I restarted it and this time I've had the Traffic England website up for a couple of minutes with no crash.

I see you are running Lucid/10.04 which has Firefox 3. Perhaps an issue with the earlier version of FF? I don't know. I don't have time to investigate this atm - must go out - but I will have a play with this website in Lucid, Maverick and Natty this evening (if I find time) and let you know how I get on.

It's a useful site. I will bookmark it. In the meantime you might find this one meets your needs and it's never played up for me on any versions of FF:

[Transport Direct]("http://www.transportdirect.info/Web2/Home.aspx?NRMODE=Published&NRORIGINALURL=%2fTransportDirect%2fen%2f&NRNODEGUID=%7B9B2CEBBB-B2D4-4022-A0D1-5B939541864D%7D&NRCACHEHINT=Guest&repeatingloop=Y")

It has live travel news if that is what you want.

---

### Post by coffeecat on 2011-05-08
> **coffeecat said:**
>  I will have a play with this website in Lucid, Maverick and Natty this evening (if I find time) and let you know how I get on.

> **Man_Beach said:**
> All I get is a blank area with "Wait for applet to be loaded..."?

Posting from Lucid. The main page loads OK. If I click on the M25 button, for example, I get a map of the M25 but then get the "wait for applet to be loaded" message as you do. That's when, in Natty, the M25 map zoomed out to the whole of the UK and then zoomed back down to the magic roundabout again.

Perhaps it's an issue with the version of icedtea6-plugin used in Lucid.

**EDIT**: I get the same "wait for applet to be loaded" in Maverick as well. But as posted before, the site works in Natty with FF4.

---

### Post by Man_Beach on 2011-05-09
Ah well - at least it's not me. I'll have to use Opera!!!

---

