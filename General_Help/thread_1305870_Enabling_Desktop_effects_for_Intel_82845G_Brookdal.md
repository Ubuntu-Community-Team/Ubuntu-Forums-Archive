---
title: "Enabling Desktop effects for Intel 82845G Brookdale?"
date: 2009-10-30
forum: General Help
---

### Post by JorgeGon on 2009-10-30
Hello. I am new to Ubuntu (Got swept in by all the Karmic talk!), and have recently installed Karmic Koala.
    
    The only problem I'm having so far is that I can not enable Desktop Visual Effects. i was wondering if there was a way to enable them..
    
    Onboard graphics card is: Intel 82845G Brookdale-G/GE (rev01).
    OS: Karmic Koala (Ubuntu).
    
    Any help would be greatly appreciated.

---

### Post by leizz on 2009-12-08
Have You find any "remedy" for this issue?

---

### Post by doixanh on 2009-12-08
Your chipset is probably blacklisted. Try unblacklisting it first.

---

### Post by leizz on 2009-12-08
Ok. Thanks, never done that before, but i will google it! :)

---

### Post by JorgeGon on 2010-01-02
[quote=leizz]
Have You find any "remedy" for this issue?
[/quote]



No a remedy was never found for this issue. Honestly, I don't think it will ever be fixed.

[quote=doixanh]
Your chipset is probably blacklisted. Try unblacklisting it first.
[/quote]

It is blacklisted. If you disable the blacklist and then try using desktop effects it'll do nothing but freeze.

---

### Post by leizz on 2010-01-02
Thank You Guys.

Remedy for me was changeing hardware, works fine :)

---

### Post by JorgeGon on 2010-01-04
A little update on this..

I've managed to get Desktop effects working on my Intel 82845G Brookdale. I can even get the "Extra effects" enabled, and no problems so far.

What I did was added my appropiate monitor settings (unrelated to the issue but mentioning anyway) to my xorg.conf along with defining how much Videoram to use, and by setting acceleration method to UXA. After that I disabled the compiz blacklist, and this time it actually worked WITHOUT freezing. So yeah. I can now finally use that Firepaint feature. :P

---

### Post by maxpowers43 on 2011-06-02
it would be appreciated if you would post your xorgconfig so newer users know how to do all that without googling each settings syntax

---

