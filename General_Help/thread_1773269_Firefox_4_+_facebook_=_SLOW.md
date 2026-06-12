---
title: "Firefox 4 + facebook = SLOW"
date: 2011-06-01
forum: General Help
---

### Post by asuastrophysics on 2011-06-01
Hey guys,

For some weird reason, my computer gets extremely slow with Firefox 4 running. If I have 7+ tabs up, browsing facebook, and using either facebook chat or browsing friends photos, my CPU usage soars to 100% and the whole computer will lock up momentarily. This happens while sending/receiving chat messages and while clicking on the "next" arrow in a photo album. The computer will do this regardless of what other applications are running.


I've got an AMD Althlon 64 X2 5600+ dual core processor with 4 gigs of RAM, although Ubuntu apparently only recognizes 3 of the 4 gigs. Regardless of why Ubuntu refuses to recognize the full potential of my hardware, I'm only using 32% of my RAM with firefox open in the aforementioned state. Desktop effects are completely disabled, and I have an nVidia GeForce 8600GT graphics card.

Any ideas why it's running so slow?

---

### Post by collisionystm on 2011-06-01
> **asuastrophysics said:**
> Hey guys,

For some weird reason, my computer gets extremely slow with Firefox 4 running. If I have 7+ tabs up, browsing facebook, and using either facebook chat or browsing friends photos, my CPU usage soars to 100% and the whole computer will lock up momentarily. This happens while sending/receiving chat messages and while clicking on the "next" arrow in a photo album. The computer will do this regardless of what other applications are running.


I've got an AMD Althlon 64 X2 5600+ dual core processor with 4 gigs of RAM, although Ubuntu apparently only recognizes 3 of the 4 gigs. Regardless of why Ubuntu refuses to recognize the full potential of my hardware, I'm only using 32% of my RAM with firefox open in the aforementioned state. Desktop effects are completely disabled, and I have an nVidia GeForce 8600GT graphics card.

Any ideas why it's running so slow?

Recognizes only 3 gigs? Sounds to me like someone isn't using 64 bit.... time to reinstall the correct version! I am sure you will notice better performance.

If not, probably a bug in the kernel.

---

### Post by Dustin2128 on 2011-06-01
> **collisionystm said:**
> Recognizes only 3 gigs? Sounds to me like someone isn't using 64 bit.... time to reinstall the correct version! I am sure you will notice better performance.

If not, probably a bug in the kernel.
32-bit can address 4 GB. Perhaps he has a bad RAM stick? But yeah, if you're not using it, 64-bit I'd totally recommend on anything other than a pentium D. @OP see if [noscript]("https://addons.mozilla.org/en-US/firefox/addon/noscript/") speeds it up at all. I think facebook is ad heavy too, so use [adblock plus]("https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/") (best adblocker ever- even strips video ads out of youtube).

---

### Post by collisionystm on 2011-06-01
It can but not always.

Also check your flash. If your already using 64 bit you probably have 32 bit flash installed. Big mistake. Install flash aid from Firefox addons, or download 64 bit flash from adobe

---

### Post by pqwoerituytrueiwoq on 2011-06-01
+1 flash aid 
also use adblock plus to remove the flash ads flash is bad enough without flash ads eating at your cpu much less with ads using it
alternatively you can probably find a add striper for facebook on userstyles.org
edit:
```
uname -m
```
if that does not say
*x86_64*
you are using 32 bit

---

### Post by asuastrophysics on 2011-06-01
> **collisionystm said:**
> Recognizes only 3 gigs? Sounds to me like someone isn't using 64 bit.... time to reinstall the correct version! I am sure you will notice better performance.

If not, probably a bug in the kernel.

Thank you for your reply! It's definitely a 64bit OS though.```
jakob@jake-desktop:~$ uname -m
x86_64

```

It's probably a bad stick of RAM. That might be why I sometimes get a BlueScreen in Windows for "memory management"

But why is firefox running so slow? Surely 3gigs is enough to load 9 tabs...

---

### Post by collisionystm on 2011-06-01
> **asuastrophysics said:**
> Thank you for your reply! It's definitely a 64bit OS though.```
jakob@jake-desktop:~$ uname -m
x86_64

```

It's probably a bad stick of RAM. That might be why I sometimes get a BlueScreen in Windows for "memory management"

But why is firefox running so slow? Surely 3gigs is enough to load 9 tabs...


Its crippling your motherboard. Rip that **** out of there

---

### Post by asuastrophysics on 2011-06-01
> **collisionystm said:**
> Its crippling your motherboard. Rip that **** out of there

Will it really damage it? Alright, be back on here in 10 minutes. Gotta find out which RAM stick it is. Thanks for the tip. Brb. 
 
Also, I'll try installing flash aid to see if that helps 

Thanks again! ;)

---

### Post by collisionystm on 2011-06-01
> **asuastrophysics said:**
> Will it really damage it? Alright, be back on here in 10 minutes. Gotta find out which RAM stick it is. Thanks for the tip. Brb. 
 
Also, I'll try installing flash aid to see if that helps 

Thanks again! ;)


No perm. Damage but it will impact performance.

---

### Post by pqwoerituytrueiwoq on 2011-06-01
all stick may be good could be a bad slot on the mobo
so when you find the suspected bad stick try it in another slot

---

### Post by asuastrophysics on 2011-06-01
Something very strange is going on here...I re-seated all the RAM modules, but it didn't really change anything. I have 3 RAM modules installed -> 1x2GB stick and 2x1GB sticks.

In the bios, 4GB of RAM is detected. If I boot Ubuntu or Ubuntu memtest, it only shows that there are 3GB of RAM, and therefore won't even try to test the suspected "bad" module. If I boot Windows 7 x64 from the other partition and click on system information, it says:
Installed Memory (RAM): 4.00GB (3.00GB usable)

I'm somewhat perplexed here. Does this still appear to be a bad memory problem or does it seem like maybe something in the bios is to blame?

---

### Post by linuxinstalledfromhdd on 2011-06-01
If your memory is limited, I suggest you try a respin of Ubuntu like Madbox:

[http://madbox.tuxfamily.org/](http://madbox.tuxfamily.org/)

It's a live disc or usb installation as well. You can make a Live USB with your Ubuntu Startup Disc Creator very easily and in a couple of minutes have that up in right in no time. :) 

Give a try. 

:popcorn:

---

### Post by Dustin2128 on 2011-06-01
> **linuxinstalledfromhdd said:**
> If your memory is limited, I suggest you try a respin of Ubuntu like Madbox:

[http://madbox.tuxfamily.org/](http://madbox.tuxfamily.org/)

It's a live disc or usb installation as well. You can make a Live USB with your Ubuntu Startup Disc Creator very easily and in a couple of minutes have that up in right in no time. :) 

Give a try. 

:popcorn:
3 gigs of ram is hardly limited. Anyway, what I'd try is removing all your ram sticks, then booting with only one in until you can't boot due to lack of memory.

---

### Post by asuastrophysics on 2011-06-01
I think I have uncovered the underlying problem.

After doing a bit of research, I'm beginning to suspect that my motherboard does not support "memory remapping". Because of this, it doesn't forward the correct RAM amount to the OS's :(

sigh. I'll try a Bios update to see if it clears this up. I really wish the Ubuntu forums would allow me to give positive feedback for everyone that helped me out here. Thanks a lot!! :guitar:

---

### Post by ElQanah on 2011-06-26
> **asuastrophysics said:**
> I think I have uncovered the underlying problem.

After doing a bit of research, I'm beginning to suspect that my motherboard does not support "memory remapping". Because of this, it doesn't forward the correct RAM amount to the OS's :(

sigh. I'll try a Bios update to see if it clears this up. I really wish the Ubuntu forums would allow me to give positive feedback for everyone that helped me out here. Thanks a lot!! :guitar:

I'd like to know how it went with it.  In my case I have Ubuntu 11.04 with Firefox 5.0 and the issues you mentioned with Facebook are the same as mine.  I have full Unity + Compiz working on my Ubuntu 32bit.  4Gbs of RAM are recognized just fine by my OS through my PAE kernel and everything works great.  Even if I open Facebook on Google Chrome browser, it works very good, very fast.  Just FF seems to be flaky about it.

---

