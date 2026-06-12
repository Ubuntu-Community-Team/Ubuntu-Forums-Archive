---
title: "xubuntu-restricted-extras now blank screen"
date: 2012-05-14
forum: General Help
---

### Post by Bucky Ball on 2012-05-14
Hi all,

Setting up my old 10.04 install (Xubuntu) and installed xubuntu-restricted-extras. 

I restarted the machine this morning and booted in to 10.10 for the day. I switched the machine off for awhile then booted into 10.04 to continue fiddling. After I choose the 10.04 kernel, goes through some normal screen things then just stops on a black screen. And that is it. 

I have a couple of other working installs and can still boot to whatever so if anyone knows how I might be able to tackle this from a working install (I can access the 10.04 install from either of the other two installs). I'm guessing it would be impossible (or tedious) to remove xubuntu-restricted-extras whilst booted into another install ...

Anyhow, all suggestions and advice gratefully accepted ...

PS: Last nightI noticed I was running 10.04.2 rather than 10.04.4 (even after updating/upgrading) and was about to start trying to fix that. Could the .2 have anything to do with my woes?

---

### Post by rai4shu2 on 2012-05-14
I don't suppose you left in the older kernel in the 10.04 install?

---

### Post by Bucky Ball on 2012-05-14
Yea but not sure how that could be the issue. It has been absolutely fine (since I've been using that kernel) until I installed some things. I'm not booting from any other kernel but the working 2.6.38 so unsure how it might effect things having other kernels installed. The other kernels work fine (2.6.32), too, just can't install my wireless drivers in them.

A have a zillion kernels hanging about my installs and never had an issue involving that. ;)

---

### Post by Bucky Ball on 2012-05-14
Just looking at the log files in the 10.04 install from the booted 10.10 install. Is there something I can check in there to see what is going wrong on the 10.04 boot? I tried boot.log but didn't tell me much. ;(

---

### Post by rai4shu2 on 2012-05-14
What about dmesg?

---

### Post by Bucky Ball on 2012-05-15
> **rai4shu2 said:**
> What about dmesg?

Couldn't find anything of relevance. I'll post it a little later to see if anyone else can ...

---

### Post by Bucky Ball on 2012-05-15
Please find the dmesg from the 10.04 LTS boot attached. If anyone wants any other logs or anything else, just ask.

I can reinstall 10.04 but have done a bit of configuring on this one already and rather not, last resort.

* Update: My dmesg is too big and exceeds the maximum upload limit for the forum so won't let me post. Anyhow, there was nothing I could see but not professing I'm any kind of whiz. Could be missing something obvious.

My bet is still on something in xubuntu-restricted-extras. How can I uninstall that (or perhaps other apps that may be causing the issue) without booting into the OS?! :-k

---

### Post by Bucky Ball on 2012-05-15
Okay, something interesting. I just booted into the 10.04 to see if anything had miraculously changed. It hadn't, but I did notice that it hits the black screen where I should be seeing the login screen, then just sits there. So, I decide to do what I would normally do - hit return, type in my password, hit return again - and the laptop whirrs and the hard drive light flickers *exactly the way they do in the working 10.10 boot*.

The install seems to be all happening, I just can't see it; it is a graphics issue. Perhaps xubuntu-restricted-extras installed something third-party graphik-ey and that has screwed me.

---

### Post by Bucky Ball on 2012-05-15
Update: Adding 'quiet splash nomodset' to the 10.04 kernel line at boot takes me to a purple screen (but I do see '10.04' flash up first). Then it sits there. Adding 'acpi=copy_dsdt' - which is what I am using in the 10.10 install - gives me the same result. 

Issue is, it was working fine before and I hadn't diddled with this stuff at all previously ... perplexed.

---

### Post by Bucky Ball on 2012-05-15
Just thought of something else and this could more likely be the problem.

I tried to install the ATI graphics drivers via 'Additional Drivers' but got an error message that it couldn't install; sorry, forgot the exact error. I didn't think anything more about it until I switched the machine off. Any graphics changes must have happened when I turn the machine back on.

Anyone any idea how I might check whether this driver is installed (or partly) and remove it via the 10.10 install???

In /usr/share/ati on the 10.04 install I have amdcccle. Should I delete that , I wonder? There was no ATI driver installed (I don't use it in 10.10) but appears there is something in there in the 10.04 install now, even though I was informed the driver hadn't installed when I tried. ;(

* Update: Not only did I remove the 'amdcccle' directory but I removed the 'ati' directory that contained it on the 10.04 install. Reboot, still nothing. Black screen.
* PS: ... and incidentally; there is no 10.04 recovery kernel listed when I boot nor is there one I can enable when I look in Grub Customizer when I'm in 10.10 (the 10.10 grub is running the show). This makes it a little trickier; can't try booting into safe mode or fixing packages from the recovery kernel.

---

### Post by Bucky Ball on 2012-05-16
Well, the beat goes on ...

When I boot and get to the blank screen, which I'm assuming is the login screen but I just can't see it, I hit ctl+alt+F1. I thought I had a black screen before. When I do this key combination the screen goes even blacker! But no cursor or anything else. If I log in blindly and 'startx' nothing happens; if I hit ctl+alt+F7 it does nothing, doesn't take me back to the not so black screen or anything else ... just sits there. 

I'm stumped but will keep digging awhile longer before I kill this 10.04 LTS install and try again. ;(

---

### Post by rai4shu2 on 2012-05-16
I could never get 10.04 to work on my machine. I don't suppose you could just install 12.04?

---

### Post by Bucky Ball on 2012-05-16
10.04 LTS was working faultlessly for months. I didn't use it much but never had any issues, unlike yourself.

I have no interest in 12.04 LTS at the moment. I'll be waiting a few months before going there is not longer (I have planned to do the upgrade or install when 10.04 reaches EOL in a year).

* Just one other point. When I try to boot the other 10.04 kernels (I have a couple of 2.6.32-** kernels also) I get exactly the same result! So I can't boot any of the 10.04.4 kernels. Whatever's happened it's killed them all. 10.10 and 11.04 boot fine. I will try the 10.04.3 kernels later (I have a couple of them also) and see if I get the same blank screen. This is c**p and driving me nuts. The only way out of the blank screen is to hold the power button and hard shutdown ... not good.

---

### Post by Bucky Ball on 2012-05-18
Here's the                                           xsession-errors.old file. The ~/.xsession-errors file is empty.

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_AU. Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default. /usr/bin/startxfce4: X server already running on display :0 <stdin>:1:3: error: invalid preprocessing directive #Those <stdin>:2:3: error: invalid preprocessing directive #or <stdin>:3:3: error: invalid preprocessing directive #Xft <stdin>:4:3: error: invalid preprocessing directive #Xft xrdb:  "Xft.hinting" on line 13 overrides entry on line 6 xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7 xrdb:  "Xft.antialias" on line 47 overrides entry on line 11 xrdb:  "Xft.hinting" on line 48 overrides entry on line 13 xrdb:  "Xft.rgba" on line 49 overrides entry on line 12 xrdb:  "Xft.hintstyle" on line 50 overrides entry on line 14 xrdb:  "Xft.dpi" on line 51 overrides entry on line 10 xfdesktop[1326]: starting up (xfce4-mixer-plugin:1338): xfce4-mixer-plugin-DEBUG: mixer_plugin->track_label = 'Master' GNOME_KEYRING_CONTROL=/tmp/keyring-rXlagx GNOME_KEYRING_CONTROL=/tmp/keyring-rXlagx  (polkit-gnome-authentication-agent-1:1399): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'  (polkit-gnome-authentication-agent-1:1399): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed GNOME_KEYRING_CONTROL=/tmp/keyring-rXlagx SSH_AUTH_SOCK=/tmp/keyring-rXlagx/ssh ** (nm-applet:1397): DEBUG: old state indicates that this was not a disconnect 0  ** (xfwm4:1321): WARNING **: Unhandled keyboard shortcut xscreensaver-command: xscreensaver window unexpectedly deleted.
```Any ideas?

PS: Not sure why my code is all on one line. Sorry about that.

---

### Post by Bucky Ball on 2012-05-21
Bump and last shot ...

Still get nowhere whenever I have another crack. Tried just about everything I've found online.

---

