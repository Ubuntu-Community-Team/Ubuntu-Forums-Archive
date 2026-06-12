---
title: "Hardware Profiles"
date: 2009-10-15
forum: General Help
---

### Post by ade234uk on 2009-10-15
I have two PC's. One at home, and one at the office.

Sometimes I need the option to work from home.

I am going to buy 2, 3.5 removable bay for my hard drive, so I can swap it between the Office and Home machine.

What I wanted to know is how do you set up Hardware profiles in Ubuntu?

---

### Post by P4man on 2009-10-15
You dont. You dont need to.

The only potential pitfall is binary drivers. If one machine has nvidia graphics, and the other not, installing nvidia drivers is going to be a problem. But even that can be solved. I modified my USB key install (full install, not a live cd) to detect the videocard, and load a different xorg.conf for ATI or nVidia cards. I have yet to find a machine that will not boot from that stick :)

---

### Post by ade234uk on 2009-10-15
Thats excellent. Another thumbs up for Ubuntu.

I though it would be like XP where you had to select a hardware profile before logging in.

---

### Post by P4man on 2009-10-15
for those interested:

```
#!/bin/bash
# copy appropriate xorg.conf for your videocard
cp /etc/X11/default.conf /etc/X11/xorg.conf
if lspci | grep "VGA compatible controller: nVidia" 
then
	# nVidia card
	nvidia-xconfig
fi
if lspci | grep "VGA compatible controller: ATI Technologies" 
then
	# ATI card, loading opensource ati driver
	cp /etc/X11/ati.conf /etc/X11/xorg.conf
fi
```

Save it as /etc/rc2.d/S01nvidia-xconfig
Make it executable.
Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf
And modify one that loads ati driver (i use the opensource) and save it as /etc/X11/ati.conf
install nvidia drivers (on a machine with nvidia graphics), and off you go. 

I guess it may give problems if you try it on a machine with an old nvidia card no longer supported by the 185 drivers, but other than that, works fine.

---

### Post by oldfred on 2010-07-20
This post was about two different video cards with a USB install.

Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

---

### Post by gpwil1 on 2011-03-04
oh my awesome!

ok now how to apply to a live USB....

---

### Post by Herman on 2011-03-27
:) Brilliant script! Works perfectly and automatically, even for LUKS fully encrypted USB installations. 
It is bash poetry for its brevity and the amount of effectiveness it achieves in just a few short lines. Really cool! 
This script should be more widely known. 

EDIT: (three months later) - For some reason I am finding that although this arrangement does work quite well, around 50% of boot-ups result in an unsatisfactory resolution for the first login, but if I log out the proper resolution is restored and then I can log back in again with the desired resolution. I wish it would boot to the right resolution every time. I am doing some reading and trying a few experiments to see if i can find a solution.

Regards, Herman :)

---

### Post by Capelare on 2012-02-22
Hi! I know that this post is from '09 and the last reply is from almost a year ago, but this is the closest I've found to a solution.

I have followed the steps described by P4man and everything seemed to go fine until just after I installed the nVidia Drivers and my USB wouldn't even boot on the machine with the ATi graphics card (monitor going to sleep)... After I managed to boot, the terminal wouldn't find fglrxinfo nor aticonfig, so I decided to uninstall nvidia drivers and right after that fglrxinfo was already on the path, and after a reboot everyhing seems to work fine (on the ATi machine, of course).

Any ideas on how to be able to install and drivers for a Radeon HD 4650 and a nVidia GeForce GTS250 **on different computers, not at the same time**.

I have Ubuntu 11.10 installed on a USB flash drive and I need to be able to boot and use it at home as well as at work.

Thanks a lot!
Capelare.

---

