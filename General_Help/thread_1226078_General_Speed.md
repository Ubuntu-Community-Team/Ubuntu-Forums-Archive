---
title: "General Speed"
date: 2009-07-29
forum: General Help
---

### Post by St Nabi on 2009-07-29
Hi all, 

This is just a small observation but I would appreciate it if someone could verify / confirm it for me.

When I download stuff whilst using Ubuntu all other windows seem to slow down somewhat.

With windows I did not really get this problem unless the connection was slow anyway and I was using Azureus/Vuze to download something at the same time.

Views welcome

Regards

St Nabi

---

### Post by wojox on 2009-07-29
Yes, any time I try doing other things while downloading bittorents my computer crawls.

---

### Post by St Nabi on 2009-07-29
Thank you, Matter confirmed.

---

### Post by CatKiller on 2009-07-29
> **St Nabi said:**
>  When I download stuff whilst using Ubuntu all other windows seem to slow down somewhat.

It depends on what you're using to do the downloading. If you're using something that takes a lot of processor time (like an inefficient BitTorrent client, for example, or something that needs to decrypt packets) then you'll have less processor for everything else. Similarly for memory usage; if whatever you're using to download things takes up a lot of RAM then there will be less for everything else and so the system will have to use swap, which is significantly slower.

---

### Post by scouser73 on 2009-07-30
I've not noticed any decreased download speed.  I would guess that your ISP are throttling your connection: [[COLOR="Red"]**Broadband Throttling**[/COLOR]]("http://en.wikipedia.org/wiki/Bandwidth_throttling").

---

### Post by GoldenSun on 2009-07-30
> **scouser73 said:**
> I've not noticed any decreased download speed.  I would guess that your ISP are throttling your connection: [[COLOR=Red]**Broadband Throttling**[/COLOR]]("http://en.wikipedia.org/wiki/Bandwidth_throttling").

throttling only affects your internet connection.  Not "other windows" as prescribed in the first post.  And usually only aimed at bittorrent traffic.  

Google released a proggy called glasnost that helps determine if throttling is occurring.  
[http://www.measurementlab.net/measurement-lab-tools#glasnost](http://www.measurementlab.net/measurement-lab-tools#glasnost)

---

### Post by St Nabi on 2009-07-30
Exactly, throttling only affects your internet connection speed not the actual system speeds. My downloading speed is just fine.

---

### Post by St Nabi on 2009-07-30
Is Azureus/Vuze an innefficient BitTorrent Client? That is what I use. Would it be better to use the Transmission BitTorrent Client that is within the application of Ubuntu itself?

---

### Post by CatKiller on 2009-07-30
> **St Nabi said:**
> Is Azureus/Vuze an innefficient BitTorrent Client? That is what I use. Would it be better to use the Transmission BitTorrent Client that is within the application of Ubuntu itself?

I have no idea. I use Transmission sometimes and a CLI client sometimes and don't have any problems with either. You could use top or system monitor to compare the two and see if one of them has higher CPU/RAM usage than the other.

---

### Post by zarqoon on 2009-07-30
I have not used azureus in a long time but I have noticed several java apps using way more cpu then they do if one uses windows. I do not know why that is but that could make for your difference. Also azureus used to need a lot of cpu every time it was not minimized to tray. Try using a client that is not java based.

---

