---
title: "Can't get sound on Dell"
date: 2010-05-31
forum: General Help
---

### Post by macrocheesium on 2010-05-31
Hey guys, I recently set up Ubuntu on my Dell Dimension 1100, and it's working perfectly, besides having no sound. The problem is, I need a driver, but can't find it. The driver I used with XP is the ADI 198x Integrated Audio. I downloaded the installer from Dell's website and ran it with Wine, but that didn't work. I need a way to get this driver on Ubuntu, without having to use an exe. Thanks!

Edit: Oh, and I looked on ASLA project, but they don't have the brand ADI!

---

### Post by macrocheesium on 2010-05-31
bump...

---

### Post by macrocheesium on 2010-05-31
C'mon community, I need help. =(

---

### Post by macrocheesium on 2010-05-31
bump again...

---

### Post by XubuRoxMySox on 2010-05-31
Hello,

Welcome to Linux! I use Xubuntu rather than Ubuntu, and fixed my sound problem by removing PulseAudio and replacing it with Esound.

I cannot say if it will work on Ubuntu, so before you try it, give others a chance to offer their ideas. It would also be really helpful if you post your computer's specifications.

And be patient. I know it's hard when you're just trying out a whole new OS, but it's a national holiday in the US and alot of folks who might be here to help are engaged in precious family time today.

Just finished my first year as a Linux user,
Robin

---

### Post by rtimai on 2010-05-31
I may be wrong, but I think you're taking your own solution to a community which would take a completely different direction to fix your problem. I've never heard of anyone installing a Windows sound driver in Linux using Wine. 

I'm no expert, but I think you'd get more help if you tried posting in the Dell areas in the Ubuntu Support Forums.

---

### Post by lidex on 2010-05-31
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Zerocool Djx on 2010-05-31
what version of ubuntu you using?

---

