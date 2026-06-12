---
title: "Intel GS45 GMA4500MHD"
date: 2011-07-30
forum: General Help
---

### Post by davemackintosh on 2011-07-30
Firstly hi everyone, its about time I signed up here been using Ubuntu for yonks now and love it.

But I've just bought and had delivered my new laptop, a Packard Bell Easynote TK37 which has the notoriously unsupported Intel GS45 chipset with the GMA4500MHD graphics card which I stupidly didnt check before.

I need to install the drivers as this 1024x768 is killing me, I can't find the drivers anywhere and the Intel site is only distributing Windows executables.

Can anyone point me in the right direction, I've looked for 4 hours now. :(

---

### Post by Sergius14 on 2011-07-30
I have a Laptop with the same Video Card.

I don't need any special driver (just open source)... and works everything. Compiz. Mplayer (xv), etc.

Ubuntu 10.04 LTS

```
glxgears 
3593 frames in 5.1 seconds
3628 frames in 5.0 seconds
4086 frames in 5.0 seconds
3558 frames in 5.0 seconds
4148 frames in 5.0 seconds
```

---

### Post by Sergius14 on 2011-07-30
You can try to update X drivers from PPA...

Just add this PPA [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

And update only Intel drivers. Then you can disable that PPA to avoid future issues.

---

### Post by davemackintosh on 2011-07-30
Forgive me, but I have never had to use a PPA so how do I install what I need from that the instructions on that link did absolutely nothing..

Its worth noting I have Ubuntu 11.04 32 bit

---

### Post by davemackintosh on 2011-07-30
Hi guys, anyone able to help or point me in the right direction?

---

### Post by gandaran on 2011-07-30
> **davemackintosh said:**
> Forgive me, but I have never had to use a PPA so how do I install what I need from that the instructions on that link did absolutely nothing..

Its worth noting I have Ubuntu 11.04 32 bit
try ubuntu 10.04 or 10.10 (or the 11.10 beta) because 11.04 has problems with some Intel video cards.
and forget that PPA repo as it only contains drivers for Nvidea and Ati cards

---

### Post by Mark Phelps on 2011-07-30
> **gandaran said:**
> and forget that PPA repo as it only contains drivers for Nvidea and Ati cards

Actually ... from the folders I saw, there WERE Intel drivers as well -- but, they were from 2009. So most likely, they would not have worked, either.

---

### Post by davemackintosh on 2011-07-30
So I tried installing 11.10 and I couldn't even get it booted up. Bit premature I think lol. I really need some help with this. Installed 11.045 again and will keep Googling.

---

### Post by davemackintosh on 2011-07-30
Anyone?

---

### Post by davemackintosh on 2011-07-30
Hi guys,

Well I installed 10.10 and it worked perfectly, I'll wait for 11.04 to be ok or even 10.10 to work with it before upgrading, I just installed the Unity interface so its all good.

Thanks for the help. :popcorn:

---

