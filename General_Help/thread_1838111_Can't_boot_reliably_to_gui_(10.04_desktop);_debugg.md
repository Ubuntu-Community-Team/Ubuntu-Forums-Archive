---
title: "Can't boot reliably to gui (10.04 desktop); debugging tips welcomed"
date: 2011-09-03
forum: General Help
---

### Post by Wim Sturkenboom on 2011-09-03
I need some debugging tips. Running Ubuntu 10.04 on a system with a nVidia 8400 based card and the nvidia 260.something driver (the last time I tried the recommended driver from the repositories, it did not work).

About 50% of the time, a boot does not get the system to the graphical environment. Removing 'quiet splash' in the grub boot line, it usually 'hangs' at 'checking battery state OK'. <ctrl><alt><F1/2/3/...> does not get me to a console in that situation.

Replacing 'quiet splash' by 'text' gets me 100% reliable to a console where I can run 'sudo service gdm start' after login and I get reliably to the normal GUI login screen.

Added --verbose to the grub boot line does not reveal anything obvious (on screen or in the log files).

**Any debugging tips are appreciated.**

---

### Post by dino99 on 2011-09-03
try the recovery mode & select "repair packages"

then:
sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure nvidia-current
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure gdm

sudo reboot

---

### Post by Wim Sturkenboom on 2011-09-03
Thanks for the reply.

Before I start those commands ;)

_*sudo apt-get install -f*_ fixes broken packages; I don't have any as far as I know (synaptic and apt-get don't complain) ; is there a way to check if I have?

*_sudo dpkg-reconfigure nvidia-current_* will reconfigure nvidia-current which I probably don't even have installed at this stage (using 260.something driver from nvidia website)

*_sudo dpkg-reconfigure jockey_*; what is jockey? no man page found for it

---

### Post by decrepit on 2011-09-03
I've got 10.04 without nVidia, and I get a similar problem.
Probably not as bad as 50%, I'd say more like 20% of the time.
I haven't tried removing "quiet splash" so not sure just when it hangs.
But it's usually when "Ubuntu" at the bottom of the screen gets to the 2nd "u".
The last time it happened I noticed a green flash as the Ubuntu screen first appeared.

So don't assume this is necessarily associated with nVidia.
I'll have a go at commenting out "quiet spash" and see where it hangs.

---

### Post by Wim Sturkenboom on 2011-09-03
@decrepit

glad to see I'm not the only one ;) I have the green 'flash' as well; don't think it's related as it also happens when I can succesfully boot.

Because upstart works event driven, it might well be that there is something that was started earlier and is waiting for something that's not happening that actually causes the 'hang'. That's why I added the --verbose in the grub bootline, but I don't see much wrong (as far as I can judge with my limited knowledge of upstart).
So what you see might not be what you get :D

---

### Post by decrepit on 2011-09-04
OK I've commented out "quiet splash", if you haven't solved this by the time mine plays up again, I'll come back with my hang point.

---

### Post by decrepit on 2011-09-22
weird, since I've commented out quiet splash I haven't had a problem.

---

### Post by jdneate on 2011-09-22
Hi - I am not techy but my experience may help you ...

I tried to update from 8.04 to 10.04 two weeks ago; I pressed the upgrade button first - the resulting system was fragile - kept freezing.

Over the next couple of days I tried all the current versions of Ubuntu and Xubuntu; they all ran perfectly off the liveCD but when loaded resulted in systems which either wouldn't boot or froze soon after starting.

4 days ago ( in despair) I loaded a system off the alternate CD - it worked first time and hasn't frozen since. It is excellent.

My only unresolved problem is setting the display to a higher resolution.

My computer/monitor are old; the driver is an old nVidia; the monitor lacks the facility for automatic setting of resolution.

---

### Post by diego_maniacco on 2012-01-19
Same issue on 10.04 LTS on two different pc. Installed openssh on both. Was able to ssh from running pc to gui-frozen pc, where I found a running system with exception of hal daemon (hald) and all following processes. A remote reboot made gui-frozen pc run fine till normal logon screen. I did get a process list in both situation for later compare.

---

### Post by Wim Sturkenboom on 2012-05-16
The 8400 eventually died and was replaced with a another nVidia card (520 or so if I'm not mistaken).

After that the problem did not happen again.

I will not mark it as solved as it actually is not solved with the original card.

---

