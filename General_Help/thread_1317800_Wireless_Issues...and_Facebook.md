---
title: "Wireless Issues...and Facebook"
date: 2009-11-07
forum: General Help
---

### Post by solwic on 2009-11-07
I have two problems I'd like to ask help about:

1.  My wireless card keeps dropping me.  Sometimes it's every couple of minutes, other times it's hours between drops.  I hate to say this, but the card works fine in Windows XP (this machine is dual-boot).  I'm using whatever generic driver came installed.  

2.  I can't use the Facebook apps/games in Opera 10.  They work fine in Firefox.  They load fine in Opera, but I can't click on anything in the Flash area once they load.  Youtube works fine with Flash; only Facebook has issues.  Any ideas?

I'm running Ubuntu 9.04, AMD Athalon64 CPU, 2.0ghz, 1.5MB RAM and an nVidia GeForce 8400GS PCI-E video card (512MB).

Thanks!

---

### Post by nikgare on 2009-11-07
Which wifi acrd are you usiong?
Post the output from **lspci | grep Ethernet**

(THere are other people in these forums with similar flash menu problems, please do a quick search for solutions to your 2nd problem).

---

### Post by solwic on 2009-11-07
> **nikgare said:**
> Which wifi acrd are you usiong?
Post the output from **lspci | grep Ethernet**

(THere are other people in these forums with similar flash menu problems, please do a quick search for solutions to your 2nd problem).

lspci | grep Ethernet gives me this:

```
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

But I think that's the onboard LAN...I'm using a PCI wireless card, which I'm pretty sure is this one:

```
02:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```

And I spent an hour scouring Google last night for a solution to the second problem.  If a solution exists, I can't find it.  

Thanks!

---

### Post by mo.reina on 2009-11-07
re. your first problem.  have a look at this thread and see if the terminal solution works for you
[http://ubuntuforums.org/showthread.php?t=1316264]("http://ubuntuforums.org/showthread.php?t=1316264")

---

### Post by buzzmandt on 2009-11-07
try wicd
> sudo apt-get install wicd
it will replace nm-applet

---

### Post by solwic on 2009-11-07
> **mo.reina said:**
> re. your first problem.  have a look at this thread and see if the terminal solution works for you
[http://ubuntuforums.org/showthread.php?t=1316264]("http://ubuntuforums.org/showthread.php?t=1316264")

Thanks, I'll check it out.

> **buzzmandt said:**
> try wicd

it will replace nm-applet

Will try that as well.  Thanks a bunch.  :)

---

### Post by solwic on 2009-11-07
So far, wicd is working.  Gonna give it a while before marking anything as solved.

Anybody have any ideas about the Opera/Facebook issue?  That one's not a problem so much as a minor annoyance, but I'd still like to sort it out.

Thanks for the help, guys.  :)

---

### Post by solwic on 2009-11-07
Quick question:  wicd shows no notification icon, up there with volume control and pidgin....  

Should it?  Can it?  I'd like to be able to monitor signal strength at a glance, if I can.

---

### Post by ElSlunko on 2009-11-07
Flash can be temperamental on my system to. First word of advice would be to get the 64 bit version if you're running karmic 64. If that's not the case or it doesn't work there is a work around I've been using. Basically you right click and hold it down. While holding it down you're able to left click on flash related items again. I think it's actually a bug in compiz.

---

### Post by julianb on 2009-11-07
> **solwic said:**
> Anybody have any ideas about the Opera/Facebook issue?  

My approach would probably be to wait for a new version of Opera or use another browser. 

Flash and Java seem to work great on the latest Chrome-for-Linux. If you give it some time, Chrome might become the most intuitive / easy-to-get-stuff-done web browser you've tried. (my main reason for using it over firefox is that chrome is quicker, especially when you're low on RAM.)

---

### Post by solwic on 2009-11-07
> **solwic said:**
> So far, wicd is working.  Gonna give it a while before marking anything as solved.

Anybody have any ideas about the Opera/Facebook issue?  That one's not a problem so much as a minor annoyance, but I'd still like to sort it out.

Thanks for the help, guys.  :)

Well, wicd is dropping me more than the other thing, and when I remove wicd, I still have no notification tray icon showing me rather I'm connected or not.  

Any solutions to this?  Would/could this be a driver issue?  Do I need ndiswrapper and the linksys driver for my card?

Thanks.

---

### Post by solwic on 2009-11-07
Who needs a good laugh?

Turns out, when I moved the PC from one room to the other last night, the antenna on the back of the tower came halfway unscrewed.  I tightened it up, and not only have I not been disconnected since, but my download/upload speed has more than tripled.  A wise man once said that sometimes the problem rests between the keyboard and the chair, and in this instance, that is so.

As for the Facebook thing...the only thing I really liked about Opera were the side tabs with thumbnail previews.  Turns out, you can get those in Firefox too, with a little plugin called Side Tabbar.  Installed it, enabled it, and now I can have my side tabs, and Facebook, too.  

So I guess the only question left is this:  how can I get a tray notification with wcid?  I hate not knowing if I'm connected or not.  

Thanks for all the input, guys.  :)

---

