---
title: "Getting past freeze on 9.10 first boot - nvidia"
date: 2010-02-19
forum: General Help
---

### Post by gbarney on 2010-02-19
Hi All,

This took me a long time to get working so I wanted to share.

First the problem: I had installed Ubunto 9.1 on my AMD Athlon 3800+ 64 bit with an Nvidia GeForce 7800 GT. I have dual monitor setup. On my first boot I could not get past more then a few seconds of the GNOME desktop (with circular mouse icon) before the whole machine froze.  That's no keyboard input or anything.

Here's what I did to fix it: (all from recovery mode)
First, I found out that I had to remove my second monitor, for some reason there's a bug out there with two monitors on 9.10.
Second, I ran apt-get update, update dist, and upgrade.
I ran apt-get nvidia-glx-185 (I tried a bunch but this is the one I installed last).

Now I was able to control the mouse for a few seconds before it froze. When I started firefox then it hangs/freezes.

Finally tried to go to System->Administration->Nvidia X Server settings.  It said I couldn't use it until I ran nvidia-xconfig.  I rebooted,ran nvidia-xconfig, and lo and behold - Ubuntu and GNOME work fine!

I have to say it's VERY annoying that the people who put together Ubuntu got rid of the X11 config file... it's fine if they upgrade to something new but in my case it broke the whole gui.

---

