---
title: "How to go from navidia to ATI gpu?"
date: 2010-03-23
forum: General Help
---

### Post by _sAm_ on 2010-03-23
Hi

I have a nvidia card in my pc, but are going to change it to a new from ATI. I have installed the latest driver from nvidia and know how I can uninstall it. But I don't know how to activate the default gpu driver in Ubuntu(called vesa?), can you tell me? Last time I uninstalled the nvidia driver I got a text only screen.

I am using Karmic 64b. 

Thanks for any help

---

### Post by new_tolinux on 2010-03-23
My wild guess: uninstall the nVidia driver, shutdown the machine and then swap the cards.
I think Ubuntu will find some new hardware and find some drivers itself.

Tried something like that in Jaunty and it worked like a charm

---

### Post by _sAm_ on 2010-03-23
Ok, thanks will give it a try. Hope I not have to reply from Lynx next time:-)

---

### Post by realzippy on 2010-03-23
...you will regret this.

---

### Post by 3rdalbum on 2010-03-23
> **realzippy said:**
> ...you will regret this.

I concur. Nvidia is at least two years ahead of ATI in terms of good Linux support.

Anyway, just remove the "nvidia-glx-185" package, remove the Driver line from your xorg.conf (if it exists, it might not) and then stick the ATI card in and you'll be alright.

---

### Post by _sAm_ on 2010-03-23
> I concur. Nvidia is at least two years ahead of ATI in terms of good Linux support.

You were right; I uninstalled the nvidia driver and installed latest driver for ATI(Catalyst 10.2). I have a graphic screen but in down right corner I have a new symbol saying "Unsupported hardware"... Compiz don't work and so on. And I even checked before I got this card that it would work(asked on some forums), damn... Buying hardware for Linux can be hard. 

The new card is more quiet then the old one, about twice as fast, works fine in Windows7 - but the linux drivers(catalyst 10.2 and the default in Ubuntu&#347; "Hardware drivers") are bad.

I join the camp that hopes AMD gives us something better in the next version of Catalyst.

Thanks again for your help:-)

---

### Post by pbrane on 2010-03-23
BTW,
```

dpkg-reconfigure -phigh xserver-xorg

```
will reset your X config to default.

So you installed the AMD proprietary linux drivers for your card and they don't work? I assume the install configured /etc/xorg.conf for you? You should look at the X server log in System->Administration->Log File Viewer and see what warnings and errors you get. You would think that the driver would work if they say it will.

---

