---
title: "live cd eliminate opening screen"
date: 2012-02-12
forum: General Help
---

### Post by avi.levi99 on 2012-02-12
Hi,
I am running Ubuntu 11.10 from an "iso" file using "Virtaul Box". It works great. My only "problem" is that every time I do it, I get the opening screen that says "Try Ubuntu" or "Install Ubuntu".
I of course always click on the "Try" option.
I was wondering if there is any way to skip that step and always get the "Try" option automatically.
I want to launch the virtual machine and have it load the ubuntu completely without me having to intervene.

Is there perhaps a different ".iso" file that I can try?

Thank you

---

### Post by mcduck on 2012-02-12
If you are using VirtualBox, why wouldn't you just make an actual install of Ubuntu into a virtual machine instead of just running the live image all the time? That way you could actually configure the system, install programs etc. and the changes you make would stay for the next time you boot the virtual machine...

---

### Post by avi.levi99 on 2012-02-12
I understand what you are saying.
However, I do need the ability to run the live CD without the installation.

Thank you
Avi

---

### Post by mcduck on 2012-02-12
In that case the answer is no, as doing that would require making a change to the boot process, which you can't do since it's a live CD and thus by definition not changeable.

(well, you probably can do it if you remaster the disk image to do what you want, but that sure isn't going to be easy. Making a proper install and perhaps disabling the users from making any changes to it would be much better option, if that's why you want to run the live environment instead of a normal one)

---

