---
title: "What can I do to speed up an older laptop?"
date: 2012-01-11
forum: General Help
---

### Post by s1mp13m4n on 2012-01-11
Hello everyone. I am using an older Gateway laptop for when I am away from home. It is not my main computer. It has these specs:

Intel Celeron M 1.5Ghz
1.2GB RAM
20GB HDD

It is running Ubuntu 10.04LTS  The hard drive has 14.1GB free. I just use it for watching DVDs, Internet, email, etc. What can I do to speed it up without spending much if any money on it? Again I use this laptop only when away from home a few times a year....it is a backup laptop so to speak. Thanks for the help.

---

### Post by Lars Noodén on 2012-01-11
The main boost came from the RAM you added.  1-2GB is great for most purposes.  If you want it to feel more responsive you could stop using a full desktop environment and use instead only a Window manager.  If that is interesting, then you could look at Openbox, FVWM-Crystal, Fluxbox, or metacity.  They can be a little harder to configure than the desktop environments but worth it for speed.

---

### Post by dak0 on 2012-01-11
**Lubuntu** uses LXDE, which is an extremely light desktop  environment (even lighter than Xubuntu's Xfce) and is ideal for very  low-memory systems (128 MB of RAM).

sudo apt-get install lubuntu-desktop

---

### Post by Double.J on 2012-01-11
> **s1mp13m4n said:**
> Hello everyone. I am using an older Gateway laptop for when I am away from home. It is not my main computer. It has these specs:

Intel Celeron M 1.5Ghz
1.2GB RAM
20GB HDD

It is running Ubuntu 10.04LTS  The hard drive has 14.1GB free. I just use it for watching DVDs, Internet, email, etc. What can I do to speed it up without spending much if any money on it? Again I use this laptop only when away from home a few times a year....it is a backup laptop so to speak. Thanks for the help.

I think the biggest advantage would be from using s new desktop environment such as LXDE - or a lubuntu install. The best perfomance I get is from live distro's such as Puppy or SliTaz
but these are live distro's not full blown installs so there's limitations there. Crunchbang is a very good minimal install based on debian using openbox as a DE.

In terms of hardware, I'm not sure you really need to do anythin - I'd be VERY surprised if 10.04 is doing much sawpping at 1.2GB RAM? though you could look at your ram sticks - I'm assuming it's got 2 if you've ended up with 1.2GB? see if one's faster than the other - both would run at the speed of the slower. Also check to see if the sticks are the same size - I suspect they aren't - RAM sticks work best in mached pairs - speed and size? I doubt it's worth the money of legacy RAM upgrade - you're just not going to use more than 1.2GB on basic linux desktoping.

The hard drive may be something to look at? 20GB is quite smallso you may be able to find a larger/fast/bigger cached drive on ebay not too expensivly. - again not really worth looking into SSD - the cost is just too high for an old laptop, and I'd image you've got an IDE gdrive anyway.

As I say, starter for 10 - see what performance change you get by trying lighter DE's

All the best :)

---

### Post by Mark Phelps on 2012-01-11
If by "speed up", you mean switch to a destkop that responds faster, then changing desktops to a lighter-weight one will help.

But, if you mean either surfing the web "faster", or having videos play more smoothly (if they lag or jerk right now) -- quite honestly, there's not really anything more you can do.

Low power PCs can benefit greatly by adding system memory, but since you already have more than 1GB, even if you CAN upgrade to 2GB (or more), I really doubt you'll see an improvement in "speed".

As to getting a bigger drive, your PC is probably limited in both the drive controller interface and the maximum size.  I have a really old laptop that came with a 20GB drive (IDE) and the most it would handle was 80GB.  So, even if it DOES allow a larger drive, given the existing controller interface limitations, once again, you're not going to see any improvement in performance with a larger drive.

Sorry, but a 1.5GHz CELERON is a very low-end processor and you're not going to see any real improvement in actual performance of the PC.

---

### Post by pr3zident on 2012-01-11
> **dak0 said:**
> **Lubuntu** uses LXDE, which is an extremely light desktop  environment (even lighter than Xubuntu's Xfce) and is ideal for very  low-memory systems (128 MB of RAM).

sudo apt-get install lubuntu-desktop

+1 lubuntu works good on all my old systems

---

### Post by s1mp13m4n on 2012-01-11
Thank you all for the help. Here is what I mean by slow....From a fresh reboot it takes 10-15 seconds for Firefox to load, I have visual effects set to none and when switching from window to window you can see the window minimize to the taskbar which takes 1-2 seconds. I know the laptop will not be a spped machine but just want it to run more smoothly. Video playback from the HDD is fine but if you click on an .avi from the HDD it can take 10-15 seconds to load and the videos do not skip or jump.

---

### Post by snowpine on 2012-01-11
> **s1mp13m4n said:**
> Thank you all for the help. Here is what I mean by slow....From a fresh reboot it takes 10-15 seconds for Firefox to load, I have visual effects set to none and when switching from window to window you can see the window minimize to the taskbar which takes 1-2 seconds. I know the laptop will not be a spped machine but just want it to run more smoothly. Video playback from the HDD is fine but if you click on an .avi from the HDD it can take 10-15 seconds to load and the videos do not skip or jump.

If things are slow loading that points to read time from the hard drive. Do you have a SSD in your budget?

Software solutions, check your swap usage. You want it to be as low as possible, if it's creeping up then check your "swappiness" (yes that is the actual technical term). I think there is a program called "preload" that speeds the launch of apps like firefox, but I've never used it, perhaps worth a forum Search.

---

### Post by s1mp13m4n on 2012-01-11
I am in the process of trying the lighter GUI maybe that will help a bit. The HDD is the stock 20GB model and it is IDE.

---

### Post by snowpine on 2012-01-11
> **s1mp13m4n said:**
> I am in the process of trying the lighter GUI maybe that will help a bit. 

I agree that's a good idea, personally I've squeeze a little extra life out of old hardware with openbox or fluxbox.

---

