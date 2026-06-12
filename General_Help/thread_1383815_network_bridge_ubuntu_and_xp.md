---
title: "network bridge ubuntu and xp"
date: 2010-01-17
forum: General Help
---

### Post by yobird42 on 2010-01-17
I'm trying to connect my ubuntu desktop to another desktop with xp on it and bridge the connections. Wireless works fine on xp but my adapter won't work on ubuntu so this is the reason why I'm trying this. I connected an ethernet cord between the two computers but it says local area connection unplugged on both computers. I connected the xp desktop to my xbox and the bridge worked fine. What's going on here?

---

### Post by jamesisin on 2010-01-17
You need to use a cross-over cable to connect two machines directly.  Alternatively, you could attach them through a hub or router which will manage the crossing-over for you.

---

### Post by yobird42 on 2010-01-17
> **jamesisin said:**
> You need to use a cross-over cable to connect two machines directly.  Alternatively, you could attach them through a hub or router which will manage the crossing-over for you.


I was thinking that but why would the xbox work without one? I'll connect a spare router I have laying around and see if it works. Thanks for the tip.

---

### Post by jamesisin on 2010-01-17
It's only a guess, but maybe the XBOX nic has cross-over capabilities built into it?  Would make sense since MS would anticipate that folks would try to attach to it without a hub or router or switch.

---

### Post by yobird42 on 2010-01-17
ok so I've got a router between the two computers and now they each recognize that the other exists, however, the ubuntu desktop has no internet. What should I do now?

---

### Post by jamesisin on 2010-01-17
Well that opens a nice can of worms.  What exactly are you trying to do?

If you want to use your XP machine as an Internet gateway for your Ubuntu machine, then you'll need to enable Internet Connection Sharing:

[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

However, I would recommend setting it up the other way (using the Ubuntu machine as the gateway for your Windows machine).

But really, what's it all about?  This is getting into some network weirdness which might be best avoided if another solution exists.

---

### Post by yobird42 on 2010-01-17
> **jamesisin said:**
> Well that opens a nice can of worms.  What exactly are you trying to do?

If you want to use your XP machine as an Internet gateway for your Ubuntu machine, then you'll need to enable Internet Connection Sharing:

[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

However, I would recommend setting it up the other way (using the Ubuntu machine as the gateway for your Windows machine).

But really, what's it all about?  This is getting into some network weirdness which might be best avoided if another solution exists.


Let me better explain my situation...

I have a linksys wusb54gc v3 usb network adapter. It's not compatible with ubuntu, I've tried. I have an older computer with xp on it, a dell dimension 4550. The adapter is installed and running fine on it. I thought I'd bridge the ubuntu desktop off the wireless on the dell. The dell is so old it doesn't automatically crossover the connections as we have just discovered. I would just use wireless on the ubuntu computer, but I have not been able to get that working. 

Something's not right here. 
[IMG]http://img34.imageshack.us/img34/6829/networkh.png[/IMG]

---

### Post by jamesisin on 2010-01-17
And you can't use that router as a gateway for both machines?

Is wireless your only option?

NIC's are pretty cheap to come by; you might be best to toss a couple of dollars at an Ubuntu compatible card.

---

### Post by yobird42 on 2010-01-17
> **jamesisin said:**
> And you can't use that router as a gateway for both machines?

Is wireless your only option?

NIC's are pretty cheap to come by; you might be best to toss a couple of dollars at an Ubuntu compatible card.

yes wireless is the only option unfortunately. Are there any linux compatible usb adapters I can go pick up at my local best buy? All the linux compatible adapters I've seen are on some shady online store.

---

### Post by jamesisin on 2010-01-17
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

and

[http://www.xaprb.com/blog/2007/11/28/favorite-usb-wireless-card-for-ubuntu/](http://www.xaprb.com/blog/2007/11/28/favorite-usb-wireless-card-for-ubuntu/)

That should give you a good start.

---

### Post by yobird42 on 2010-01-17
> **jamesisin said:**
> [https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

and

[http://www.xaprb.com/blog/2007/11/28/favorite-usb-wireless-card-for-ubuntu/](http://www.xaprb.com/blog/2007/11/28/favorite-usb-wireless-card-for-ubuntu/)

That should give you a good start.

Thanks. I appreciate your help.

---

### Post by jamesisin on 2010-01-17
Hope it works out well for you.

(You'll probably want to mark the thread as SOLVED under Thread Tools above.)

---

