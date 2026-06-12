---
title: "ERROR no room on ep ring"
date: 2011-12-22
forum: General Help
---

### Post by sj1410 on 2011-12-22
Hi,

I am getting this errors continuously in dmesg, i am not able to find the reason for this and also need a fix for it. Need help.

xhci_hcd 0000:02:00.0: ERROR no room on ep ring
hub 6-1:1.0: activate --> -12


--

---

### Post by jerrrys on 2011-12-23
Never had this happen, but found this:

[https://www.google.com/search?client=ubuntu&channel=fs&q=ERROR+no+room+on+ep+ring&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ERROR+no+room+on+ep+ring&ie=utf-8&oe=utf-8)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ERROR+no+room+on+ep+ring&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ERROR+no+room+on+ep+ring&sa=Search&cof=FORID:9)

---

### Post by sj1410 on 2011-12-24
> **jerrrys said:**
> Never had this happen, but found this:

[https://www.google.com/search?client=ubuntu&channel=fs&q=ERROR+no+room+on+ep+ring&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ERROR+no+room+on+ep+ring&ie=utf-8&oe=utf-8)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ERROR+no+room+on+ep+ring&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ERROR+no+room+on+ep+ring&sa=Search&cof=FORID:9)


already searched the google, but this does not give me any solutions

---

### Post by skan on 2012-03-02
Hello

Maybe it doesn't have anything to do with your problem but I had a similar issue, the same message with a different number, today while booting Backtrack
And the reason of the problem was that I had a Wifi card connected to my USB 3.0
I changed it to the older USB port and everything worked.
The real solution would be to solve the problem with that USB3.

---

### Post by Khayyam on 2012-03-03
> **sj1410 said:**
> I am getting this errors continuously in dmesg, i am not able to find the reason for this and also need a fix for it. Need help.

xhci_hcd 0000:02:00.0: ERROR no room on ep ring
hub 6-1:1.0: activate --> -12

Does the USB slot fail? This post on the [Linux Kernel Mailing List]("https://lkml.org/lkml/2011/12/28/188") explains why the error messages occur (specifically the patch included in the kernel sources, and what it is attempting to provide). I imagine the driver is in heavy development, as USB3 is fairly new on the scene, and so I'll no doubt print debug information for some time.

Anyhow, it may not be as fatal as it sounds.

best ... khay

---

