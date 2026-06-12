---
title: "video driver issues with 10.04 HELP PLEASE"
date: 2010-05-02
forum: General Help
---

### Post by Hobodavel on 2010-05-02
Is ubuntu, xbuntu or kubuntu still friendly to low end machines as i have a mecer (223ll0) laptop with: 
1GB of ram,
2GHz single core processor,
Intel(R) 855GM Chipset (8MB shared memory)

but having problems with installing 10.04 as it cant even reach installation the screen goes black.

Please Help..

---

### Post by GSF1200S on 2010-05-02
> **Hobodavel said:**
> Is ubuntu, xbuntu or kubuntu still friendly to low end machines as i have a mecer (223ll0) laptop with: 
1GB of ram,
2GHz single core processor,
Intel(R) 855GM Chipset (8MB shared memory)

but having problems with installing 10.04 as it cant even reach installation the screen goes black.

Please Help..

Yeah, Ubuntu will run on that hardware ok. I might suggest using LXDE if you really want a super fast desktop, because 1GB of RAM can get taken up quickly if you multitask and run memory hungry apps.

As to why the LiveCD is hanging: Incorporation of Plymouth, which tries to make the boot sequence look better, has caused many issues for people with proprietary (and even non-proprietary) drivers. The easiest way to get rolling:
1) Boot the LiveCD to the language selection screen and select your language
2) Highlight (but dont select) Try Ubuntu Without Installing and press escape
3) Go down to the kernel line which ends with:
```
ro quiet splash
```
and change it to:
```
ro i915.modeset=0
```
and then press enter. Hopefully it will boot for you then. Good luck :)

---

### Post by Hobodavel on 2010-05-02
(i am trying this from a xubuntu disk)
after i click on esc i get a confirmation message asking if i want to go to leave the graphical boot menu and start the text mode interface. i then select okay, but then it asks for a kernel image, so i am not sure where to follow your instructions:

> **GSF1200S said:**
> Yeah, Ubuntu will run on that hardware ok. I might suggest using LXDE if you really want a super fast desktop, because 1GB of RAM can get taken up quickly if you multitask and run memory hungry apps.

As to why the LiveCD is hanging: Incorporation of Plymouth, which tries to make the boot sequence look better, has caused many issues for people with proprietary (and even non-proprietary) drivers. The easiest way to get rolling:
1) Boot the LiveCD to the language selection screen and select your language
2) Highlight (but dont select) Try Ubuntu Without Installing and press escape
3) Go down to the kernel line which ends with:
```
ro quiet splash
```and change it to:
```
ro i915.modeset=0
```and then press enter. Hopefully it will boot for you then. Good luck 

---

### Post by GSF1200S on 2010-05-02
> **Hobodavel said:**
> (i am trying this from a xubuntu disk)
after i click on esc i get a confirmation message asking if i want to go to leave the graphical boot menu and start the text mode interface. i then select okay, but then it asks for a kernel image, so i am not sure where to follow your instructions:

Hmmm.. I dont know if the Xubuntu disk is any different. I installed from an AlternateCD. Its hard for me to picture what you are talking about. I would suggest using your other OS for now and I will download the LiveCD image and see how to do it within virtualbox (this will take some time and I need to sleep).

---

### Post by Hobodavel on 2010-05-03
I have over come my problem with 10.04 through booting recovery mode > fail safe graphics 
But now how can i fix the video card problem,
Or set my grub to always boot into recovery mode

Any help please!!

Thanks for help thus far.

---

### Post by Hobodavel on 2010-05-03
can i modify my video card drivers for it to boot normally so that i don't need to boot in fail safe mode...??:confused:

---

### Post by sotirovlyu on 2010-06-25
To all who'll stumble open this thread, correct options is:

```
i915.modeset=1
```

or at least this one worked for me.. according to: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

