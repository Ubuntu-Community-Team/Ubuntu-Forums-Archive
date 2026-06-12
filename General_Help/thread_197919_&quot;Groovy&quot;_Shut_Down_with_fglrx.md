---
title: "&quot;Groovy&quot; Shut Down with fglrx"
date: 2006-06-16
forum: General Help
---

### Post by Mau on 2006-06-16
This has been happening since breezy, but I was too lazy to ask about it --

After spending hours getting fglrx configured correctly for my ATI card, whenever I shut down I do not see the convential splash screen.  Instead, my monitor starts to make rainbow colors with the pixels visible.  It looks like the monitor is full of a colorful liquid and it starts to absorb.  The computer powers off fine and starts up.  Everything works perfectly, but it is only after I shut down or reboot.

If this can be fixed, great.  If it cannot, so what.  (I'm open to suggestions).  But, do you think this is damaging my hardware at all?  When I use the MESA drivers, this does not happen.

---

### Post by eth on 2006-06-16
I've had the very same issue on Breezy. ATI gave no support, and there was no way to solve it, but everything worked ok. 
But with the latest xorg-server-fglrx package installed BEFORE making the full configuration with ATI proprietary drivers (yes, install the package and then redo all the way throught the full config) the problem seems solved: now I have no issues of any kind.

---

### Post by Mau on 2006-08-11
Ok, now that I'm using Compiz/Xgl, it's getting very painful to switch back to metacity by shutting down.

I've done more research, and it appears this is called a "bleed" through or something.  The result still stays the same: I see weird colors as if my computer was on hallucinogenics and the computer is unusable, but not frozen (I can still hear sound).

So, I'm looking for a fix.  Using Dapper and all up-to-date.  My card is ATI 9600 Pro.

EDIT: fglrxinfo is telling me the OpenGL version string is 8.25.18, but the latest from ATI is 8.27.x.  When will the reps be updated?

---

### Post by Mau on 2006-08-11
Looked into it more, and it seems to be a problem when xserver restarts. Ctrl+Alt+Blackspace causes my problem to occur.  Could it be a problem loading the driver when it restarts? ](*,)

---

### Post by juliohm on 2008-05-06
I had the exact same issue on my HP DV6445us laptop.

I ran through [this tutorial]("https://help.ubuntu.com/community/FixVideoResolutionHowto") and, as it turns out, all I had to do is the following:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
md5sum /etc/X11/xorg.conf |sudo tee /var/lib/x11/xorg.conf.md5sum
sudo dpkg-reconfigure xserver-xorg
```

Hope it helps!

In fact, this is what I used to get every time I shutdown/hibernated:

[IMG]http://juliohm.googlepages.com/IMG_0855.jpg[/IMG]

After running those command lines and reconfiguring xorg, it all came back to normal now.

---

