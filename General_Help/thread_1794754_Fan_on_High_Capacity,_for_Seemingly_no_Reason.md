---
title: "Fan on High Capacity, for Seemingly no Reason"
date: 2011-07-01
forum: General Help
---

### Post by jlacroix on 2011-07-01
Hello everyone, I am having a strange problem and need some help troubleshooting. I have a Dell Latitude E6410 laptop with integrated Intel graphics, and I use Kubuntu 11.04 (64-bit). 

Right now, as I type this, the fan is on at what I assume is it's loudest, and has been loud like this for the past 20 minutes non stop. I currently have running Firefox (since I'm typing this post) a Konsole window, and a Dolphin Window.

This doesn't make sense, considering my CPU usage isn't maxed out (it's less than 10% most of the time on each Core, sometimes jumping to 30% and back down) and it's only using less than 1GB of my 8GB of RAM. I checked to see if the CPU's are throttling properly, and each of the four cores is running at only 1199mhz. I also regularly clean my laptop of dust and debris. To make it short, I see no logical reason why my fan should be on full blast. The air coming out of the vent is barely even luke warm.

This has been happening for a while, but I haven't had a chance to troubleshoot until now due to spending all my free time studying for Linux+ (which I passed, yay!)

Edit: I forgot to mention that the reason I didn't post the temperature of my laptop is because lmsensors isn't compatible, and cannot read any temperature sensors.

---

### Post by pawhtiobo on 2011-07-01
Hi,

I had a similar issue with an E4200, after i upgraded my BIOS to the last available and upgraded also my VGA driver the problem was gone...

See ya....

---

### Post by jlacroix on 2011-07-01
> **pawhtiobo said:**
> Hi,

I had a similar issue with an E4200, after i upgraded my BIOS to the last available and upgraded also my VGA driver the problem was gone...

See ya....
I already have the latest BIOS installed, but the video driver is whatever Kubuntu provides. Did you update to something other than what the distribution includes?

---

### Post by wolfen69 on 2011-07-01
Try a couple different live cd's and see if the problem persists. Then we can go from there.

---

### Post by pawhtiobo on 2011-07-01
Hi,

If my memory is right, i updated my driver (Intel) from this repository:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

You can also try to reset the BIOS the default settings...

You can also check this threads i found:

[http://forum.notebookreview.com/linux-compatibility-software/505721-linux-fan-always.html](http://forum.notebookreview.com/linux-compatibility-software/505721-linux-fan-always.html)

[https://bbs.archlinux.org/viewtopic.php?id=112572](https://bbs.archlinux.org/viewtopic.php?id=112572)

See ya...

---

### Post by jlacroix on 2011-07-01
> **pawhtiobo said:**
> Hi,

If my memory is right, i updated my driver (Intel) from this repository:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

You can also try to reset the BIOS the default settings...

You can also check this threads i found:

[http://forum.notebookreview.com/linux-compatibility-software/505721-linux-fan-always.html](http://forum.notebookreview.com/linux-compatibility-software/505721-linux-fan-always.html)

[https://bbs.archlinux.org/viewtopic.php?id=112572](https://bbs.archlinux.org/viewtopic.php?id=112572)

See ya...
Thanks, maybe I'll try that repository. The last link you posted is a topic I posted back when I used Arch Linux on my laptop, but I'm convinced this is a different issue. Since switching to Kubuntu, I also switched to a SSD (so I doubt it's hard drive heat).

Do you use KDE as well? I'm wondering how your suspend/resume works with the Intel driver you linked above.

---

### Post by pawhtiobo on 2011-07-01
Hi,

I use Gnome as my primary desktop interface, i never felt in love by KDE :D....loll

I no longer have that laptop i switched to a Toshiba R700, i needed something smaller and lighter to carry around, has i can remember i always had issues with the suspend/resume and the hibernate feature, sometimes the laptop awaken in a bad mood...very slow, not responsive so I never used much that features. You can always try with a liveCD of another version of Ubuntu and see if the problem persists...

See ya....

---

