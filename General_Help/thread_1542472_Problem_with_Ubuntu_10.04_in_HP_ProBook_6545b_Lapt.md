---
title: "Problem with Ubuntu 10.04 in HP ProBook 6545b Laptop"
date: 2010-07-30
forum: General Help
---

### Post by mathewmndeme on 2010-07-30
I need help.

recently I have secured a new laptop...HP ProBook 6545b with windows 7. I decided to add partition in which I installed Ubuntu 10.04. It happened that whenever I unplug the power adopter then my laptop keep restarting without allowing me even to login.

I decided to install the old version...I installed Ubuntu 9.04 and it worked fine. I upgraded it to Ubuntu 9.10 and it works fine also without the rebooting problem. However, I had some problem with a vodafone USB modem....could not locate my country (Tanzania) ....so I decided to download updates and upgraded my laptop to Ubuntu 10.04 which works fine with the vodafone modem.

However, when I disconnect it from power source the machine keeps on restarting. Please help....what might be the cause of this problem? your urgent response will highly appreciated

Mathew

---

### Post by mathewmndeme on 2010-07-31
anyone to help please

---

### Post by Mark Phelps on 2010-07-31
Sorry, don't have a solution offhand ... but there have been lots of reports of 10.04 having problems with machines overheating and with power management with regards to batteries in laptops.

Looks like you're experiencing the second kind.

I didn't see any solutions in the threads that reported the battery problems.

Your best bet for the immediate future is that, since 9.10 apparently works well for you, replace 10.04 with 9.10 -- and keep that.

Version 10.10 will be coming out in a few months, and some beta versions should be available in a few weeks.

Would download one of the beta versions, burn that to CD, and boot from that using LiveCD mode -- and see how it handles your battery situation.

---

### Post by Quackers on 2010-07-31
Have you seen the 9th item in this Sticky by Phillinux?

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by mathewmndeme on 2010-08-02
I have seen it but I can not locate ***gnome-power-manager/general*** so as to deselect the line you mentioned



This is what is there

[B][I]
mathew@mathew-laptop:~$ cd .gconf/apps/
[email]mathew@mathew-laptop:~/.gconf[/email]/apps$ ls
brasero    file-roller  gnome-app-install  metacity   rhythmbox
compiz     f-spot       gnome-screensaver  nautilus   totem
eog        %gconf.xml   gnome-screenshot   nm-applet  update-manager
evolution  gedit-2      gnome-terminal     panel
[email]mathew@mathew-laptop:~/.gconf[/email]/apps$[/I][/B]

Any idea of where is ***gnome-power-manager*** directory?

Mathew

> **Quackers said:**
> Have you seen the 9th item in this Sticky by Phillinux?

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by coldraven on 2010-08-02
You get to the gconf-editor by pressing Alt+F2 which will open the Run dialogue box.
Type gconf-editor in the box and press Enter.
Then expand the "apps" tree and scroll down to gnome-power-manager.
Hope that will fix it!

---

