---
title: "China: Accessing Information"
date: 2009-08-21
forum: General Help
---

### Post by Ruthless on 2009-08-21
Hello all!

I'm not quite sure where to post this, but general informations seems the best.


I am currently living in Shanghai, China and I have run into a rather large problem. Due to the Chinese system of blocking random sites, I cannot (CANNOT) update my system - this includes my System76 driver which I need desperately. If I use Synaptic Package Manager to update, it will show a status bar for the download and then pop up a window describing how it could not connect to the server. 

As a side note, I also cannot connect to some sites like blogger and facebook and am in need of any good ways around that. I've tried a few free proxy sites, but none of them worked. 


Does anyone have any suggestions to aid me in this dilemma?

---

### Post by fishy6969 on 2009-08-21
The one option that springs to mind is setting yourself up with a VPS (virtual private server)in the US or UK and forwarding everything to it with say SSH tunnelling. With SSH at least you can change the port number of the server should the default (22) be blocked. Unfortunately these VPS's are not free. Linode offer some ubuntu solutions for about $29 per month.

Regards

---

### Post by Ruthless on 2009-08-21
Update:


I guess that the sites aren't blocked by China but by the proxy  that we go through here on campus.

Is there any way to set up Synaptic and the system76 driver updater so that they go through the same proxy as Mozilla? 

(Note: I already tried to manually configure the proxy address with Synaptic but, after accessing the internet, all of my updates failed because the "404 could not be found".)

---

### Post by michy99 on 2009-08-21
Have you tried using a different server? Go to System -> Administration -> Software Sources and change it where it says 'Download from.'

---

### Post by XCan on 2009-08-22
It sounds like you are only in China temporarily. Perhaps the easiests for you is to ask one of your friends overseas to setup a tunnel? I don't know about the details, but if you use a port that is open it should be fine.

---

### Post by 3rdalbum on 2009-08-22
For your software updates, you could try going to System > Administration > Software Sources and choosing "Find Best Server" from the Mirrors menu.

---

### Post by HiImTye on 2009-08-22
you could try either [www.proxy4china.com](www.proxy4china.com) or [www.proxy4asia.com](www.proxy4asia.com)
the great firewall of china seems to let some sites work in some cities and not for others, a proxy is likely the best choice

---

### Post by maximinus_uk on 2009-08-23
> **HiImTye said:**
> you could try either [www.proxy4china.com](www.proxy4china.com) or [www.proxy4asia.com](www.proxy4asia.com)
the great firewall of china seems to let some sites work in some cities and not for others, a proxy is likely the best choice

I also live in China (Harbin). Of course, both of those sites are blovked from here :P

However, I have no problem updating Ubuntu here. Either choose 'Find best server', as previously suggested, or just choose the US server. The Chinese server listed is a total waste of time.

In the last week or so its seem a few more sites have been added to the great firewall of China.

---

