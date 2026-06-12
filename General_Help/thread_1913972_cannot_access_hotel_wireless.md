---
title: "cannot access hotel wireless"
date: 2012-01-23
forum: General Help
---

### Post by iconoclast hero on 2012-01-23
I am in Germany and have my USB Ubuntu 10.10 drive attached to my work laptop instead of my laptop. It just spins and doesn't pick up an IP address from the DHCP server. It did briefly one time and I,m using my Windows 7.5 HTC radar 4g, so I know that the connection works. I believe that I have the proper driver installed since the hotel network is visible on my dell latitude e4300. The way that the login works is to connect to the wireless, get an IP address from DHCP and then authenticate via a browser with my room info. I would really appreciate some help with connecting.
 
Thanks

---

### Post by iconoclast hero on 2012-01-24
I'm really hoping that someone can help me sort this out.  I am presently on my computer at my company's wireless hotspot so I believe that the wireless driver is working.  Is there anything I can try to force ubuntu to take the DHCP?  Should I just try to assign a fixed ip and hope that it doesn't crash into someone else's DHCP request?  Any useful suggestions would be appreciated.

> **iconoclast hero said:**
> I am in Germany and have my USB Ubuntu 10.10 drive attached to my work laptop instead of my laptop. It just spins and doesn't pick up an IP address from the DHCP server. It did briefly one time and I,m using my Windows 7.5 HTC radar 4g, so I know that the connection works. I believe that I have the proper driver installed since the hotel network is visible on my dell latitude e4300. The way that the login works is to connect to the wireless, get an IP address from DHCP and then authenticate via a browser with my room info. I would really appreciate some help with connecting.
 
Thanks

---

### Post by holycow131415 on 2012-01-24
The hotel i visited had a webpage i needed to visit before being allowed to access the "internet". Problem was, that webpage only opened by default in IE on windows. SO i had to write the address down so that i could open it in firefox while in linux so that i could access the internet.

---

### Post by iconoclast hero on 2012-01-24
> **holycow131415 said:**
> The hotel i visited had a webpage i needed to visit before being allowed to access the "internet". Problem was, that webpage only opened by default in IE on windows. SO i had to write the address down so that i could open it in firefox while in linux so that i could access the internet.

Thanks!

I have seen that login screen...  I can get that address from my phone perhaps or the slow computer in the lobby of the hotel.  Since it does not get a DHCP assignment, I am not sure that will work, but it is worth a shot.

---

### Post by Gillingham on 2012-01-24
A thought based on my experience, have you tried different browsers?  I've tended to find that Firefox tends to play much nicer with hotel networks than Chrome.

David

---

### Post by iconoclast hero on 2012-01-24
> **Gillingham said:**
> A thought based on my experience, have you tried different browsers? I've tended to find that Firefox tends to play much nicer with hotel networks than Chrome.
 
David
 
Yeah, I just tried ff, chrome, and opera.  Still no love from the hotel WiFi.
 
I am going to see what happens if I open an XP virtual machine and try to connect.

---

### Post by iconoclast hero on 2012-02-02
From what I have been able to gather, the computer I was using worked with some routers and not others.  It is using the proprietary Broadcom STA driver and while it works at home and worked some places, it did not work uniformly with different routers in Europe.  I have not had the opportunity to test it in various locations in the US.  From the looks of it, it will be a complicated process to tweak it and almost impossible without access to a LAN connection.  The moral of the story is that I will have to take my own computer as well as the work computer with me next time I travel...unless someone can suggest a 802.11b/g/n usb stick that works well with ubuntu?

---

