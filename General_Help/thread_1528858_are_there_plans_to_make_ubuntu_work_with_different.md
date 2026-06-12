---
title: "are there plans to make ubuntu work with different devices?"
date: 2010-07-11
forum: General Help
---

### Post by alex04210 on 2010-07-11
hi
are there plans to make ubuntu work with different devices - tuners, printers, scanners, local net etc?
nothing of mine isn't working - there are no drivers. 
no for lexmark z35
no for scanner mustek bearpaw 1200 cu plus
no for tv tuner aver media 507 
no local net with sharedfolders (I don't no how install it - in windows xp local net appeared itself i have only connected my wi-fi router and gave names to the local net and pc)
it is sad - I should use Windows to have everything work good((( 

Manual searching and installing such drivers are so terribly difficult ubuntu or other linux OS is good idea to have alternative OS but it's no chance to use it for most of people - it is too difficult no make it good

---

### Post by 3rdalbum on 2010-07-11
> **alex04210 said:**
> hi
are there plans to make ubuntu work with different devices - tuners, printers, scanners, local net etc?

Drivers for most popular devices are already included in the Linux kernel (or in a relevant subsystem).

> no for lexmark z35
no for scanner mustek bearpaw 1200 cu plus
no for tv tuner aver media 507

Older Lexmark devices won't work. Newer devices are okay because Lexmark is finally making Linux drivers.

I've never heard of your brand of scanner before, which may explain a lack of driver. For printers and scanners you should stick with HP (do the scanners work on Lexmarks now? Not sure, I'd need to check).

The Avermedia Studio 507 is apparently supported. What are you using to try and scan channels and pick up signals?

> no local net with sharedfolders (I don't no how install it - in windows xp local net appeared itself i have only connected my wi-fi router and gave names to the local net and pc)

Places > Network. Double-click on Windows Network. Everything needed to browse your shares is preinstalled.

Make sure you're not running ANY firewalls on your PCs (only run one on your modem/router). If all else fails, go into your file browser and hit Control-L, and in the location bar type:

```
smb://<ip-address-of-the-server-computer>/<name-of-share>
```

It's odd that you'd describe Windows XP as working fine with your network shares and not Ubuntu. Usually Windows XP is the one you need to tell the IP address of the server to and Ubuntu can pick up all the shares on your network without you having to tell it where they are.

---

