---
title: "Help With NVIDIA"
date: 2012-01-28
forum: General Help
---

### Post by borth92 on 2012-01-28
I have a Samsung NP-RC512 Laptop and my fresh install of Ubuntu boots into Unity 2D when I select Ubuntu from the login screen. I added the repo for the latest NVIDIA Drivers (version 290.10) and am still having this issue. PLEASE HELP!!!

---

### Post by borth92 on 2012-01-28
The Graphics Card is an NVIDIA GeForce 525M. Just thought I would add that

---

### Post by wolfen69 on 2012-01-28
> **borth92 said:**
> I added the repo for the latest NVIDIA Drivers (version 290.10)
There's no need to add any repos, just install the latest driver from *additional drivers*.

---

### Post by MG&amp;TL on 2012-01-28
Two things:

1) What does the additional drivers dialog show? (Ideally, a screenshot)

2) Run:

```
/usr/lib/nux/unity_support_test -p
```
and post the output.

---

### Post by borth92 on 2012-01-28
> **wolfen69 said:**
> There's no need to add any repos, just install the latest driver from *additional drivers*.

Okay, well same principal. I added the repo that installed the most current version (with updates). Regardless, It will not let OpenGL run.

---

### Post by borth92 on 2012-01-28
Somebody please help, why would the most current NVIDIA Drivers not be able to handle OpenGL?

---

### Post by scheibenlosen on 2012-01-28
> **borth92 said:**
> Somebody please help, why would the most current NVIDIA Drivers not be able to handle OpenGL?

 Did you reboot to see if that might help?

---

### Post by Segofam on 2012-01-28
"Bumblebee works. I can use my Nvidia GeForce GT 325M GPU to activate  using Google Chrome for super fast 3D graphics accelerated web browsing.  Most of the time, it is not necessary. I am looking forward to future  improvements and refinements to the Bumblebee project and I hope that  the Ubuntu and overall GNU/Linux community will be able to utilize the  Nvidia Optimus technology as it works with Microsoft Windows 7 with  seamless graphics switching capabilities. It is definitely making  significant improvements with each new release." **Part quote from How many of you have completely switched to Ubuntu thread.**

I could be barking up the wrong tree here!!!
But then again...

---

### Post by borth92 on 2012-01-30
I will give bumblebee a shot, but I ran hard drive diagnostics and of course my Best Buy refurbished computer has a failing hard disk. Maybe the driver is installing incorrectly because of that??

---

