---
title: "ati r500 series drivers"
date: 2010-06-04
forum: General Help
---

### Post by Allen2475 on 2010-06-04
Help! New to linux/ubuntu and HAVE NOT GOT A CLUE ABOUT IT as this is the first time I've used this operating system.
I have installed ubuntu 10.4 LT on to my new harddrive (harddrive had no opperating system installed).
Now the graphics are very slow on my computer, if I log on to the internet then the web page I'm looking at does not page up/down very well and is very slow to refresh.
I think this is due to a missing graphic card driver but I am not sure how to fix it.
My computer is a Packard Bell intel Core 2 Duo, with ATi graphics, I think it is an ATi R500 series graphics card installed on my computer.
I have tried to find some information on this problem but I am in way over my head with this.
If someone could give me a step by step on how to sort this out I would be very greatfull.

---

### Post by lavinog on 2010-06-04
Open a terminal and post the output of this command:
```

lspci

```
It should list your video card.
Also use the log file viewer to post your Xorg.0.log
Use code blocks to keep the post neat (the # button, or see my sig)

The open source radeon drivers should be used automatically.
Depending on your video card, you might be able to use the proprietary drivers (currently they have better 3d performance)
R500 should be supported.

---

### Post by Allen2475 on 2010-06-10
Thanks lavinog for your reply to my post for help, sorry about not thanking you sooner for your advice but I have not had the time to get on my computer to do any thing with it.
For some reason the graphics on my computer seem to have sorted themselves out on there own (So far that is - touch wood); I don't know if this is due to the latest updates that I downloaded or what but I'm not compling. 
Again thanks for your help it was very much appreciated.

---

### Post by dino99 on 2010-06-10
you can check your driver activation into: system admin hardware driver

---

### Post by cbrunhaver on 2010-06-10
AFAIK, the R500 isn't supported by the fglrx driver any more (on this version of Xorg) and so you can either install and older verion of ubuntu (8.10, I believe) or use the open source "radeon" driver.  

This should be configured b default, though I have had to generate an xorg.conf and fiddle with a couple of settings (for KMS etc.) on certain cards.

---

### Post by lavinog on 2010-06-10
> **cbrunhaver said:**
> AFAIK, the R500 isn't supported by the fglrx driver any more (on this version of Xorg) and so you can either install and older verion of ubuntu (8.10, I believe) or use the open source "radeon" driver.  

This should be configured b default, though I have had to generate an xorg.conf and fiddle with a couple of settings (for KMS etc.) on certain cards.

You are correct, the fglrx driver seems to only support r600 and up.

---

