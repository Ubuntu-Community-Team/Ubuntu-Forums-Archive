---
title: "BURG changed my Ubuntu splash resolution"
date: 2010-07-08
forum: General Help
---

### Post by warnec on 2010-07-08
Hi. Today I wanted to get rid of ugly GRUB and installed GRUB. I really like it, but there is one annoyance - I used these tips:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

To have a Splash screen in Ubuntu in full 1680x1050 32-bit, and it worked perfectly. But when I installed BURG in the place of GRUB, I have 640x480 ugly boot splash as I had in the very beginning :(

Repeating the steps doesn't seem to help. What should I do?

PS
I tried adding this:
```

GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050x32

```
to /etc/default/burg as I read somewhere on the Internet, but ddin't help :(

I should note that I easily changed BURG's resolution to 1680x1050 using 'R' while in BURG. 640x480 only applies to Splash after I choose Ubuntu.

---

### Post by warnec on 2010-07-09
So, nobody bumped into the same problem?

---

### Post by warnec on 2010-07-09
Oh! I fixed it! The lines I have shown in the first post were correct, I just didn't know I had to run 
```

sudo update-burg

```
to apply them. Thankfully, I found that over the internet somewhere.


Solved!

---

