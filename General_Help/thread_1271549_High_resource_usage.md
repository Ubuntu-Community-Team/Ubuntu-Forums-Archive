---
title: "High resource usage"
date: 2009-09-21
forum: General Help
---

### Post by bridgetothesun on 2009-09-21
My notebook has a Intel P8700 Dual core processor and 3gb ram. Looking at the system monitor in 9.04, I'm averaging around 25-30% usage during normal web browsing and it spikes to 50% when I switch between tabs. Also, if I go to the "Processes" tab, and simply, expand the column width for "CPU" the usage spikes to 60+%!!!

What is going on?

---

### Post by bridgetothesun on 2009-09-21
I have a strong feeling this is tied to my video card (Intel 4500MHD). Compiz Fusion works great but it seems like running Firefox really slows things down for some reason.

---

### Post by bridgetothesun on 2009-09-21
any help?

---

### Post by omskates on 2009-09-21
Look in /var/log  the Xorg.0.log   Look for words like "infinite" "loop" "error" etc.  I can't diagnose any better than that I'm afraid.  I have 36% going to /var  (probably X) during idle  and probably is the video driver like you said.  I'll check back to see if you've had any luck.

---

### Post by 3rdalbum on 2009-09-21
Maybe give Opera a try. On my netbook with a pathetically-slow SSD, Firefox frequently goes dark and unresponsive, whereas Opera doesn't.

---

### Post by bridgetothesun on 2009-09-21
omskates, do you have intel graphics?

---

### Post by bridgetothesun on 2009-09-21
Am I better off going with Fedora which does support my video card?

---

### Post by omskates on 2009-09-22
> **bridgetothesun said:**
> omskates, do you have intel graphics?

No, NVidea
I can reduce this high usage with a reboot but not sure what triggers it.  I should try restarting X next time it occurs.

---

### Post by P4man on 2009-09-22
> **bridgetothesun said:**
> Am I better off going with Fedora which does support my video card?

Its not really a distribution thing, its a kernel driver issue. Perhaps fedora 11 already uses the newer kernel with the new intel gpu drivers though, Im not sure, it would surprise me. In a few weeks Karmic will be released which has it though..

---

### Post by bridgetothesun on 2009-09-22
Yeah I tried Fedora 11 64bit and had the same issue. I think I'm going to try a different distro and wait till Karmic comes out and try again. 

thanks.

---

### Post by philinux on 2009-09-22
What does the command 

```
top
``` Show when it behaving badly?

---

### Post by bridgetothesun on 2009-09-22
The command "Xorg" is using the largest percentages when I did the command "top".

Thanks.

---

### Post by bridgetothesun on 2009-09-24
Update: Got rid of 9.04 and installed 9.10 Alpha 6. Resouce usage much improved. glxgears nets me 2000fps+, a 100% improvement.

---

