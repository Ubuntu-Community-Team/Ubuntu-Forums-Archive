---
title: "how safe is ubuntu for shoping"
date: 2009-09-25
forum: General Help
---

### Post by delukard on 2009-09-25
i just installed ubuntu on my triple boot pc(xp64,7x64 and unbuntu64) i have updated ubuntu and was wondering how safe is from spyware and virus. compared to x64 with antivirus and spyboot s&d.
I ask this because i sometimes like to buy games online.
should i install an antivirus for ubuntu?(stupid and old question i suposed but i have to ask it)

---

### Post by abhilashm86 on 2009-09-25
no antivirus is required!! and no spyware, just browse with freedom:) shop and play whatever you want, always remember ubuntu and linux, kernel is written by hackers, they know all threats and easily they overcome:) 
enjoy ubuntu.............

---

### Post by pcjunkie on 2009-09-25
You have little to worry about but do be careful what you install in Ubuntu.
While no system is hackproof, Ubuntu / Linux security is as they say, not an afterthought but a process. 

I have no firewall or Antivirus and the system has been clean since day 1.
Its also a laugh to watch the occasional website trying to break in. 

"You have a virus"....

Actually. no I don't!

If you look at var/logs/ and do a little research on them you will know precisely if someone has "broken in".
Best approach is a strong password using 0-10 A-z and !(#*#$^$><) 8 to 12 characters. Very hard to break...
for e.g

E><tReM3-Dr34mZ

Remember to change it sometimes..
Use command 
passwd 
done.

---

### Post by philinux on 2009-09-25
> **delukard said:**
> i just installed ubuntu on my triple boot pc(xp64,7x64 and unbuntu64) i have updated ubuntu and was wondering how safe is from spyware and virus. compared to x64 with antivirus and spyboot s&d.
I ask this because i sometimes like to buy games online.
should i install an antivirus for ubuntu?(stupid and old question i suposed but i have to ask it)

Good resource site for other stuff too.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by delukard on 2009-09-25
thank's guys. more and more i'm loving ubuntu
i only wished there were more drivers for it,
i have 3 wireless cards that doesn't work(1 belkin n usb, and 2 dlink usb)

---

### Post by Soul-Sing on 2009-09-25
Maybe a suggestion, when shopping try to use "sites" with a http[COLOR="Red"]s[/COLOR] connection. And maybe a browser which cleans itself after surfing: clearing cookies/history/ref./etc.

---

### Post by rakete on 2009-09-25
You have to be aware of Javascript and Flash Viruses, though... You can encounter bad Javascript or Flash scripts, which could possibly steal your accounts and passwords in: Comments of Websites, Myspace, adservices, Warez-, Movie- and Pornsites and many more..

Don't panic, but be aware of this fact... 

Firefox Addons like NoScript and AdBlocker Plus can minimize the risk of such attacks.

---

### Post by scragar on 2009-09-25
> **delukard said:**
> thank's guys. more and more i'm loving ubuntu
i only wished there were more drivers for it,
i have 3 wireless cards that doesn't work(1 belkin n usb, and 2 dlink usb)

belkin use open source drivers(in fact they're all under GPL AFAIK), could you tell me what you've tried and more about the wireless card?

---

### Post by delukard on 2009-09-25
sure.
the belkin model is  F5D8053(that's the model) and TBH i haven't tried anything, i just read some ubuntu treads and apparently no one could install it.

One more question , i see that my cpu is being used 28% and 20% , just using firefox and listening to music(amd64 x2 5400) in xp64 it isn't that high.

Also does cool n quiet work in ubuntu 64(to me this is very important)
thank's for the help!

---

### Post by Vaphell on 2009-09-25
CnQ works here, you can see for yourself, just add a small thingie to the panel that shows CPU frequency (right click at panel, Add to panel, CPU frequency something ... ) - my AMD 3000+ when idle slows down to 1.0Ghz from default 1.8Ghz

---

### Post by pcjunkie on 2009-09-25
> **rakete said:**
> You have to be aware of Javascript and Flash Viruses, though... You can encounter bad Javascript or Flash scripts, which could possibly steal your accounts and passwords in: Comments of Websites, Myspace, adservices, Warez-, Movie- and Pornsites and many more..

Don't panic, but be aware of this fact... 

Firefox Addons like NoScript and AdBlocker Plus can minimize the risk of such attacks.

Addblock / Flashblock works and speeds up firefox somewhat..

> **delukard said:**
> 
One more question , i see that my cpu is being used 28% and 20% , just using firefox and listening to music(amd64 x2 5400) in xp64 it isn't that high.

Also does cool n quiet work in ubuntu 64(to me this is very important)
thank's for the help!

My AMD systems are all working fine with C & Q.

---

### Post by scragar on 2009-09-25
> **delukard said:**
> sure.
the belkin model is  F5D8053(that's the model) and TBH i haven't tried anything, i just read some ubuntu treads and apparently no one could install it.

Hmn, I can't find any threads for it in quite a while, that's strange.

I'd connect it first, then wait a while, see if it get's put to use:
```
ifconfig
```If it does then you won't need to search around, since it'll work right out of the box, otherwise you might need to use ndiswrapper, that can be a little buggy though. Better to double check it works right natively than to attempt to use ndiswrapper(since bad drivers can crash your system or cut out).

---

