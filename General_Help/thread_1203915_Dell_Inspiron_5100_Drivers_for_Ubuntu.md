---
title: "Dell Inspiron 5100 Drivers for Ubuntu?"
date: 2009-07-04
forum: General Help
---

### Post by arnold15 on 2009-07-04
[SIZE=4]I have Ubuntu 9.04 Installer and I want to Intal it to my Dell Inspiron 5100, but the problem is I dont have the compatible Drivers for Ubuntu which is Linux-based OS.. I have the drivers but its only for Windows OS.. I cnt find all the drivers which is compatible for my laptop, like the Broadcom 440x(network driver), Conexant(modem driver), Intel Mobile Chipset, Synaptics Touchpad(touchpad driver), Sigmatel Stag(audio drivers), and ATI mobility M7(Video driver).. this drivers is not compatible for ubuntu because its only exclusive for Windows XP OS, and I am searching for Drivers wich is compatible for Ubuntu.. Thanks! O:)[/SIZE]

---

### Post by sigurnjak on 2009-07-04
Forget about drivers , dude ! Just double click install and watch magic happens . 
Remember , this is not windows , it is a whole new world !
Have faith   and double click damn install  already !!!:lolflag::lolflag::lolflag:

---

### Post by jw5801 on 2009-07-04
> **arnold15 said:**
> [SIZE=4]I have Ubuntu 9.04 Installer and I want to Intal it to my Dell Inspiron 5100, but the problem is I dont have the compatible Drivers for Ubuntu which is Linux-based OS.. I have the drivers but its only for Windows OS.. I cnt find all the drivers which is compatible for my laptop, like the Broadcom 440x(network driver), Conexant(modem driver), Intel Mobile Chipset, Synaptics Touchpad(touchpad driver), Sigmatel Stag(audio drivers), and ATI mobility M7(Video driver).. this drivers is not compatible for ubuntu because its only exclusive for Windows XP OS, and I am searching for Drivers wich is compatible for Ubuntu.. Thanks! O:)[/SIZE]

Short answer, unlike installing Windows, you just don't need to find them and have them all there ready to install after you finish installing the OS, they're part of the default install already.

Long answer: Most hardware manufacturers tend not to provide Linux drivers for things. Most of the drivers we use for anything are free and open source and are contained in the Linux kernel. If you really want to, you can configure and build your own kernel and ensure that all the drivers you need get built and nothing else, however it's not necessary in the slightest. Ubuntu provides pre-built kernels which have most drivers you'll ever need built as `modules', they don't provide any runtime overhead unless they are `loaded' into the kernel during runtime. Ubuntu (and most other modern distros) use a combination of the hardware abstraction layer daemon (hal) and a device manager daemon (udev) to probe your hardware and load the appropriate modules during boot. You may need to do some configuration for things like graphics hardware, but even that is incredibly minimal these days.

---

### Post by arnold15 on 2009-07-04
Now i understand! Thanks guys! so, if i reformat my system to Ubuntu it wil surely ready to use.. No need to install thngs.. ok.. now i know.. Thanks guys! :D

---

### Post by t4thfavor on 2009-07-04
Don't count on the modem, or the wireless if it is broadcom, otherwise you will be good to go.

---

### Post by arnold15 on 2009-07-05
What if I install the Ubuntu Jaunty then the Network Driver doesnt respond??

---

### Post by philcamlin on 2009-07-05
> **sigurnjak said:**
> Forget about drivers , dude ! Just double click install and watch magic happens . 
Remember , this is not windows , it is a whole new world !
Have faith   and double click damn install  already !!!:lolflag::lolflag::lolflag:

thats so true my pc didnt need any driveers at all!

---

### Post by philcamlin on 2009-07-05
> **arnold15 said:**
> What if I install the Ubuntu Jaunty then the Network Driver doesnt respond??

then you get the driver

sorry for double post :(

---

### Post by jw5801 on 2009-07-05
> **arnold15 said:**
> What if I install the Ubuntu Jaunty then the Network Driver doesnt respond??

Your wired will be fine. Your wireless is Intel, yes? That should be fine as well. If it's not working straight away then ask on the forums (or just search, it'll almost certainly have happened before).

---

### Post by spcwingo on 2009-07-05
I just installed 8.04 (Hardy) on a 5100 a few months ago.  I just replaced the wireless card with an Intel ipw2200bg.  You can find them dirt cheap on ebay used.  You can also get the broadcom card going, but it's gonna take a little work to get it running (maybe not if it's in the restricted drivers application...not sure about Jaunty).

---

### Post by jw5801 on 2009-07-05
> **spcwingo said:**
> I just installed 8.04 (Hardy) on a 5100 a few months ago.  I just replaced the wireless card with an Intel ipw2200bg.  You can find them dirt cheap on ebay used.  You can also get the broadcom card going, but it's gonna take a little work to get it running (maybe not if it's in the restricted drivers application...not sure about Jaunty).

Broadcom wireless will work fine with a marginal amount of effort, it really doesn't take much, certainly not worth the cost of buying a new card if that's the only reason to do so!

Doesn't sound like he has a broadcom wireless chipset anyhow, just the broadcom 440x (wired) which won't present any troubles at all.

---

### Post by gunterhausfrau on 2009-08-19
ok, I've got one of these. I have two laptops, both updated from 8.04 (I think, that was the last stable, yes?) to 8.10 then to 9.04. Neither of them work wireless. I saw something about "easy with a little effort..." or some such comment. Let's assume I put in a little effort and still no luck. Any help? I've looked over the web, but not much help.

I purchased the laptop used, it was a clean install of Ubuntu from a local non-profit computer recycling place (well regarded).

help!

thanks.

---

### Post by jw5801 on 2009-08-19
> **gunterhausfrau said:**
> ok, I've got one of these. I have two laptops, both updated from 8.04 (I think, that was the last stable, yes?) to 8.10 then to 9.04. Neither of them work wireless. I saw something about "easy with a little effort..." or some such comment. Let's assume I put in a little effort and still no luck. Any help? I've looked over the web, but not much help.

I purchased the laptop used, it was a clean install of Ubuntu from a local non-profit computer recycling place (well regarded).

help!

thanks.

Making a new thread is your best bet if you really can't find anything with a search. You'll need to know and post whatever wireless card is in the machine for anyone to be able to help. Something like the output from: ```
lshw -C network
```

---

