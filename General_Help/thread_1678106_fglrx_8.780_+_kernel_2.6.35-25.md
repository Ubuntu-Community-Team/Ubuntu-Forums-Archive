---
title: "fglrx 8.780 + kernel 2.6.35-25"
date: 2011-01-29
forum: General Help
---

### Post by c0ldfusi0n on 2011-01-29
Hi guys.

I've been having this problem for a week - which forces me to use Windows, and I just can't stand it anymore, so I come to you for help.


The situation before this all happened is pretty standard. I have a HP Pavillion dv5 laptop with an ATI Mobility Radeon 4200 series. It always worked fine with Ubuntu for as long as I can remember. However, at one point, something happened and truly made a majestic mess of things. It might've been extra repos I enabled with Ubuntu Tweak - I do not know. But something made it so that my system would not boot any longer.

And when I say "won't boot", this is what I mean:
- Durning a normal bootup, any entries (except Windows) selected with GRUB (or BURG, not even sure which one I'm using anymore) will spawn the Ubuntu loading screen - then try to start X (or GDM) 5 times. The screen goes to dark, black and back to the Ubuntu loading screen. Then it just stays there until I spawn another TTY.

I have no idea what is happening or why. There are no errors in my logs, and I'm truly at a loss here.

I've linked three files: Xorg.0.log, the output of dmesg and the GDM log:

Xorg.0.log: [http://ubuntu.pastebin.com/tpVKc2tc](http://ubuntu.pastebin.com/tpVKc2tc)
dmesg: [http://ubuntu.pastebin.com/Nd5aYj45](http://ubuntu.pastebin.com/Nd5aYj45)
gdm's :0.log: [http://ubuntu.pastebin.com/FhK7ubSr](http://ubuntu.pastebin.com/FhK7ubSr)

Let me know if any of you more knowledgeable folks can restore some sanity in my life.

Any help is greatly apreciated.

---

### Post by jdoklovic on 2011-02-02
I have the same exact problem, anyway to fix it??

I'd even like to try to revert the kernel update if there's no way to fix it.

---

