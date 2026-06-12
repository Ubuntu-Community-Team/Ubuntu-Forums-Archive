---
title: "WPA settings not available in network setup?"
date: 2006-03-17
forum: General Help
---

### Post by charleyramm on 2006-03-17
I have a home wireless network that uses WPA-PSK encryption. I've been running windows XP on all machines so far, but I would like to give Ubuntu a fair chance. 

Is there a way to set my WPA key through the ubuntu network setup tool? 

If not, is there a way to do this with command line tools? I have heard a little bit about wpa_supplicant. Does this come with Ubuntu?

Thanks.
charley

---

### Post by compuguy1088 on 2006-03-17
[QUOTE=charleyramm]I have a home wireless network that uses WPA-PSK encryption. I've been running windows XP on all machines so far, but I would like to give Ubuntu a fair chance. 

Is there a way to set my WPA key through the ubuntu network setup tool? 

If not, is there a way to do this with command line tools? I have heard a little bit about wpa_supplicant. Does this come with Ubuntu?

Thanks.
charley[/QUOTE]

The best place to set up wpa_supplicant, where I found out how to set up my network is from [this guide]("http://www.ubuntuforums.org/showthread.php?t=90450&highlight=wpa_supplicant"), though there are other methods that are more complex than that one, that I have't tried....

---

### Post by charleyramm on 2006-03-18
Brilliant, the wireless connection is working! Thanks for your help. :KS 

It doesn't seem to pick up my dhcp though. Any tips?

I can configure the card manually and ping a local computer. I expect I could configure the internet gateway manually too, but I have done that before and it is hard.

 Charley

P.S. Where is a good place to make comments to the ubuntu developers about supporting WPA by default? Also, I noticed I couldn't connect to my network when the SSID was un-broadcast.  Most likely this is down to my inexperience, but I'm curious if anybody else has the same problem.

---

### Post by firecat53 on 2006-03-18
Some of the wireless drivers don't support dhcp via wpa, so you have to assign a static IP address in your /etc/network/interfaces file.

I've heard that too, about hidden SSID's, but I just can't remember the setting that allows that off the top of my head. Keep searching.....

Scott

---

