---
title: "Weird Graphical glitch"
date: 2011-03-28
forum: General Help
---

### Post by ShinIori319 on 2011-03-28
Good night all!
I don't know if this is the right forum to post this. Since some time ago, I've been having this strange glitch that is now annoying me.

It usually happens when I use **Firefox** (does not happen with other browsers like Opera or Chrome) to visit, for example, YouTube. Where it should be pitch black, screwed up parts of the video or another multimedia probram (such as Second Life) show up.
It has happened on white colors as well.

Here are some shots. I did not take them using Print Screen since, strangely, Print Screen does not seem to capture this glitch.

I am using Ubuntu 10.10 on a 1 GB nVidia 9500GT.

---

### Post by LowSky on 2011-03-28
If print screen isn't capturing the problem there is only two things that can be causing the issue. The first would be the monitor, but you said it only happens using firefox which makes this an odd issue. So the next place to check is the graphics driver. What version are you using?
you can run the newer version by adding this code which add the newer repos and updates the driver
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade
```

The place to check after that is to let us know what version of flash are you using. A quick way to fix flash is to use Flash-aid from here t hat will install the newest version and correct version for your system (32 vs 64bit)
[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

---

### Post by ShinIori319 on 2011-03-29
> **LowSky said:**
> If print screen isn't capturing the problem there is only two things that can be causing the issue. The first would be the monitor, but you said it only happens using firefox which makes this an odd issue. So the next place to check is the graphics driver. What version are you using?
you can run the newer version by adding this code which add the newer repos and updates the driver
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade
```The place to check after that is to let us know what version of flash are you using. A quick way to fix flash is to use Flash-aid from here t hat will install the newest version and correct version for your system (32 vs 64bit)
[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

Oh, nice!

I added that repository and it seemed to be that my drivers were badly outdated. I want to think that was the cause of the issue, since I have not seen anything else since. Also updated my Flash Player.
Only thing now is that Flash crashes a lot, but it gets now easily solved with refreshing the page.
Thanks a lot! :)

---

