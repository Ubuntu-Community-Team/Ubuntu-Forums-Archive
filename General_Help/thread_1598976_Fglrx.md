---
title: "Fglrx?"
date: 2010-10-17
forum: General Help
---

### Post by oxf on 2010-10-17
OK I know what the fglrx driver is but it's not enabled by default when Ubuntu is installed. It's there in Synaptic if I need it. (I have the ATI Radeon xpress 200M graphics card.)

Can someone tell me a little more about it please and why I might want to enable it? I hear it being discussed from time to time. I have had a few run of the mill video/display issues in the past, nothing major though,  so I'm wondering if I should have tried it maybe?

In what circumstances should I use it and do I need to disable the other ATI drivers first. Any infomation/tips appreciated
Thanks

---

### Post by Lazaruss on 2010-10-17
fglrx is the proprietary driver made by ATI for most of it's series of Radeon cards. Usually, the open source drivers automatically used should suffice, but if you are missing OpenGL/GLX support than you may wish to try fglrx.

You must uninstall/disable the open source drivers before using fglrx

---

### Post by Mark Phelps on 2010-10-17
Sigh ... wish folks who offer fglrx advice here would do some RESEARCH first!

That card does not have AMD propietary drivers available for it.  AMD dropped such support after Ubuntu 8.10 came out.  The only drivers that will work now are the open-source drivers, and they are installed by default during system setup.

If you try to remove the open-source drivers and install anything else, you'll only trash your display and have to spend a lot of time and work reinstalling the original open-source drivers./

---

### Post by Lazaruss on 2010-10-17
Sorry mark, my bad. Thats stuff i've picked up from other forums...

---

### Post by oxf on 2010-10-17
> **Mark Phelps said:**
> Sigh ... wish folks who offer fglrx advice here would do some RESEARCH first!

That card does not have AMD propietary drivers available for it.  AMD dropped such support after Ubuntu 8.10 came out.  The only drivers that will work now are the open-source drivers, and they are installed by default during system setup.

If you try to remove the open-source drivers and install anything else, you'll only trash your display and have to spend a lot of time and work reinstalling the original open-source drivers./

OK thanks.
So you are saying that even though Synatic describes FGLRX as "video drivers for the ATI graphics accelerators" it won't work for the Radeon Xpress and I should leave well alone?

The reason I asked was that a recent kernel upgrade broke my system. Consensus was that it broke the ATI drivers and one sugestion was that I might want to consider the FGLRX. Instead I chose to do a fresh install and move to Maverick instaead.

---

### Post by ffg1977 on 2010-11-02
Mike,
does Ubuntu 10.10 work fine with your Xpress 200M?
I tried 9.10 and 10.04, but my system freezes, so I'm using 9.04 instead.
Thanks.

---

### Post by oxf on 2010-11-07
> **ffg1977 said:**
> Mike,
does Ubuntu 10.10 work fine with your Xpress 200M?
I tried 9.10 and 10.04, but my system freezes, so I'm using 9.04 instead.
Thanks.

Yes! 10.10 is running great in this laptop with the Xpress 200M.
Just with the open source drivers included by default.

I should add that my previous comment about the kernel update braking my system is now incorrect. It seems I'm getting bad sectors on the HD and I need to replace it.

---

