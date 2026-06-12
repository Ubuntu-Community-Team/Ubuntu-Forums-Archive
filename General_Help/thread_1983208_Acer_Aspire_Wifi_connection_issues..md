---
title: "Acer Aspire Wifi connection issues."
date: 2012-05-19
forum: General Help
---

### Post by Aerowave on 2012-05-19
I just started running ubuntu on a new computer and love it. The only problem I have had so far with the os is that it doesn't find my wifi network.
I have an Acer Aspire 5755G with an i5 processor and over 1 GiB of video ram, so of course the computer hardware has no trouble running ubuntu. I can locate and access said wifi network on a windows partition that I set up, so the wifi card and drivers are working. I messed around with the ubuntu terminal for a while and found that ubuntu does in fact use my windows wireless drivers, and also discovered that my network connection status was listed as uncertain or something.
So then I tried an ethernet connection and was able to maintain a stable connection, but this is very inconvienient for me.
Based on this information, is there anything that I can do to fix the issue? I have a feeling that my wifi might just be turned off, but I don't know enough about the linux command line to be able to tell for sure...
Oh, I have also gone into the "additional drivers" application, and "no proprietary drivers are available."
Thanks!

---

### Post by PhantomTurtle on 2012-05-19
Does that mean that Ubuntu can still find other wireless connections, just not yours? If so then there should be more under something like other connections(I'm not sure exactly what it might be called, but there it will list more). If this is not the problem could you include the name of your wireless card.

---

### Post by Aerowave on 2012-05-19
Yes, I can still find other connections. I did check in the other connections directory though, and didn't see my network.

---

### Post by PhantomTurtle on 2012-05-19
> **Aerowave said:**
> Yes, I can still find other connections. I did check in the other connections directory though, and didn't see my network.

OK, then this means that it might not be a hardware problem with your laptop. Make sure that the wifi works by using another device or try a different wifi hotspot. Maybe there is something blocking the router, get closer to it.

---

### Post by Aerowave on 2012-05-19
I thought the same thing, so I tried other networks and found that I was able to connect to them. Getting closer to my wireless router, however, does nothing :(

---

### Post by PeterP24 on 2012-05-19
It happened to me also! I mean, my brother computer which runs MSWindows could detect the wifi from our router. My Ubuntu powered laptop along with my android phone couldn't detect that network - albeit they could detect every other wifi network from the neighbourhood. Having the phone connection to wifi also in the same situation, I suspected that the router settings were wrong. Was just a hunch, because I don't know anything about routers. So I started to restart the router several times and you know what? Sometimes it worked and I could access wifi for several weeks before happening again. 
This month however, it happened again and I couldn't do anything - even restarting the router didn't help. So I stayed for about a day without wifi access and then I insisted that my brother should fix the router (was his stuff!). 

He went through the settings, and the one that made wifi access possible again for me was one that forced the router to emit on a specific channel (and not choose automatically the channel).

Hope this helps!

---

### Post by latinlightning on 2012-05-19
How did you set-up your wireless router? Are you having it publicly broadcast the SSID (it's network name) or did you disable that? If the latter is the case, you would have to manually enter the correct settings for it by "Connect to Hidden Wireless Network" option.

---

