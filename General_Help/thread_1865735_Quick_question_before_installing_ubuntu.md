---
title: "Quick question before installing ubuntu"
date: 2011-10-20
forum: General Help
---

### Post by mulroydm on 2011-10-20
I am planning on installing ubuntu 11.10 onto my Dell xps 15 l502x laptop and just have a quick question regarding the nvidia graphics card.  Is it going to cause any issues?  I attempted to install natty previously and ubuntu defaulted to using the intel graphics card rather than the nvidia and would not load unity.  Is there any problems with this ins 11.10?  Or are there any ways around this?  Thanks

---

### Post by TeoBigusGeekus on 2011-10-20
Did you try disabling the intel card from bios and see what ubuntu would do?
Nvidia cards are (usually) ok with ubuntu - unless it's optimus of course.

---

### Post by Alan F on 2011-10-20
I cannot answer your question but try the Live CD option first before you install to verify if it works OK or not.

---

### Post by drawkcab on 2011-10-20
Support for Optimus is not yet available.  If you can enable discrete video only in Bios, you may be fine.  Otherwise, yeah, Linux will work with the Intel card while powering the Nvidia card for no good reason.

---

### Post by mulroydm on 2011-10-20
Yeah I believe it is Optimus, I heard there was something called bumblebee that was quick solve for the problem though?  As for running on the liveCd, Unity shows up on that but when I actually install, it goes back to using classic view or whatever it is called.

---

