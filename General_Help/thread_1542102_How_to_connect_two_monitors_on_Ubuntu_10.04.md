---
title: "How to connect two monitors on Ubuntu 10.04?"
date: 2010-07-30
forum: General Help
---

### Post by TheNerdAL on 2010-07-30
So my mom got a monitor and I wanted to connect it with another one to have dual monitors. I think I connected a DVI cable to the input of my video card and my VGA cable to the input of the video card. Now what?  Thanks.

---

### Post by TheNerdAL on 2010-07-30
Okay, so I rebooted to see if that was the problem and it booted on the other monitor with no background but when I opened Google Chrome from AWN, it went black.

---

### Post by Vaphell on 2010-07-30
what's your graphics adapter?

---

### Post by dino99 on 2010-07-30
depend on what your video card is , you need to run the config tool (nvidia-settings or aticonfig) to tweak xorg.conf

but first, remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf

then run the tool

---

### Post by TheNerdAL on 2010-07-30
```
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```

---

### Post by Vaphell on 2010-07-30
so run the nvidia-settings tool, once you run that, it will be straightforward to configure monitors.

---

### Post by TheNerdAL on 2010-07-30
> **Vaphell said:**
> so run the nvidia-settings tool, once you run that, it will be straightforward to configure monitors.

I do the basic things and hit apply but my other monitor doesn't turn on and my main monitor changes but goes back to normal.

---

### Post by TheNerdAL on 2010-07-30
Should I reboot and see if that works?

---

### Post by P4man on 2010-07-30
assuming you installed the nvidia drivers, open the nvidia settings (system > administration > nVidia X server settings). 
Go to display configuration. Click the disabled monitor, click configure, set it to TwinView. Hit apply. It should look somewhat like this:
[[IMG]http://img840.imageshack.us/img840/9518/screenshot049.th.png[/IMG]](http://img840.imageshack.us/i/screenshot049.png/)

Click save to X configuration file to make the setting permanent.

---

### Post by TheNerdAL on 2010-07-30
> **P4man said:**
> assuming you installed the nvidia drivers, open the nvidia settings (system > administration > nVidia X server settings). Click the disabled monitor, click configure, set it to TwinView. Hit apply. It should look somewhat like this:
[[IMG]http://img840.imageshack.us/img840/9518/screenshot049.th.png[/IMG]](http://img840.imageshack.us/i/screenshot049.png/)

Click save to X configuration file to make the setting permanent.

It gives me this "Failed to parse existing X config file '/etc/X11/xorg.conf'!" and this pops up: 
[IMG]http://i424.photobucket.com/albums/pp322/thenerdal/Screenshot.png[/IMG]

Just trying to be safe here. :P

---

### Post by cascade9 on 2010-07-30
sudo nvidia-settings

Or is that gksudo? Gah, easy to tell I dont use sudo much.....

---

### Post by P4man on 2010-07-30
Just go ahead and save it. Assuming its working tho?  Its just complaining something is wrong with the old one, it cant modify it so it will make a new one which is good ;).

---

### Post by P4man on 2010-07-30
> **cascade9 said:**
> sudo nvidia-settings

Or is that gksudo? Gah, easy to tell I dont use sudo much.....

that would be gksudo but since 10.04 its no longer needed. nvidia-settings will (finally!) notice its not running as root and prompt for password for sudo privileges to write xorg.conf.

---

### Post by TheNerdAL on 2010-07-30
> **cascade9 said:**
> sudo nvidia-settings

Or is that gksudo? Gah, easy to tell I dont use sudo much.....

Cascade! My hardware man! :P 

I get the same thing using both sudo and gksudo. I also get this in the terminal for both as well: 
```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

```

---

### Post by TheNerdAL on 2010-07-30
> **P4man said:**
> Just go ahead and save it. Assuming its working tho?  Its just complaining something is wrong with the old one, it cant modify it so it will make a new one which is good ;).

I saved it and my other screen doesn't do anything, should I reboot?

---

### Post by cascade9 on 2010-07-30
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

That would be because you havent set a "Default screen"

Figure out which monitor you want as the default, then tick the 'make this the primary display for the X screen' for that display.

> **P4man said:**
> that would be gksudo but since 10.04 its no longer needed. nvidia-settings will (finally!) notice its not running as root and prompt for password for sudo privileges to write xorg.conf.

I havent run 10.04 on a machine with an nidia card yet, nice ;)

---

### Post by TheNerdAL on 2010-07-30
> **cascade9 said:**
> VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

That would be because you havent set a "Default screen"

Figure out which monitor you want as the default, then tick the 'make this the primary display for the X screen' for that display.



I havent run 10.04 on a machine with an nidia card yet, nice ;)

It was already ticked. 

I rebooted and both monitors were black for a while then my main monitor booted up okay without a dock but the other one is still black.

---

### Post by P4man on 2010-07-30
Is nvidia-settings properly detecting and identifying the second monitor? If so have you tried changing the resolution and refresh rate?

There is no need to reboot no need even to save the xorg, just hitting apply should make the changes instantaneously.

---

### Post by TheNerdAL on 2010-07-30
> **P4man said:**
> Is nvidia-settings properly detecting and identifying the second monitor? If so have you tried changing the resolution and refresh rate?

There is no need to reboot no need even to save the xorg, just hitting apply should make the changes instantaneously.

I think it is.

---

### Post by TheNerdAL on 2010-07-30
I changed cables of each monitor and the other one still doesn't do anything. :(

---

### Post by TheNerdAL on 2010-07-30
So I think it's the monitor, but I'm so geeky that I want to try to use my TV as another monitor and see if that works. :P Anything I should know before I try it out?

---

### Post by TheNerdAL on 2010-07-30
Woo, I got it to work but there is a black bar at the bottom of my main monitor. :P

---

