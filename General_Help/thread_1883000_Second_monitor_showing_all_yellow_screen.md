---
title: "Second monitor showing all yellow screen"
date: 2011-11-18
forum: General Help
---

### Post by AlexBaranosky on 2011-11-18
Hi,

I'm having trouble setting up a second monitor.  It seems that no one is active at the forum I posted my question originally, so here's a link:
[http://ubuntuforums.org/showthread.php?p=11467915#post11467915](http://ubuntuforums.org/showthread.php?p=11467915#post11467915)

Original post:

[INDENT]Hello,

I recently decided to try to set my Ubuntu 10.04 desktop up with dual monitors.

I bought a new graphics card (Radeon HD 5450) and installed it. I plugged my two monitors into the new card: my larger monitor via DVI and the other via VGA. When I booted up Ubuntu showed my main monitor fine, but not the second. After going to System > Preferences > Monitors, and detecting the second, and setting it to "on", Ubuntu offered to change a config file, so I said "yes". Now the secondary monitor is showing only a single shae of yellow...[/INDENT]

What can I do to correct this?

Thanks,
Alex

Any help is really appreciated.

Alex

P.S. I've managed to get the monitor to light up in all black now, but that is hardly much of an improvement.

---

### Post by AlexBaranosky on 2011-11-18
*bump*

---

### Post by LinuxFan999 on 2011-11-18
Could you post a picture showing the problem?

---

### Post by 4Orbs on 2011-11-18
Does your mouse cursor move back and forth between the monitors as it's supposed to?

---

### Post by AlexBaranosky on 2011-11-18
No movement between monitors. Let me take a picture.

---

### Post by AlexBaranosky on 2011-11-18
Took a picture but it came out really dark. What it looks like is simply a black monitor.  However, it is actually "lit" up black, a opposed to the monitor just having no power whatsoever flowing through the screen.

---

### Post by 4Orbs on 2011-11-18
Have you activated the proprietary driver for your graphics card (in the system menu, Additional Drivers)? If there is a recommended driver and you activate it, you should be able to set up dual monitors using the Catalyst Control Center (as adminitrator). Since you are using Ubuntu 10.04, I don't know if this applies to you (I'm using 11.10)... but in order to set up dual monitors on my machine, I found it necessary to install the KDE desktop, log into KDE and run the Catalyst Control Center from that environment. This was for X/L/Ubuntu; all three needed KDE to get working duals.

---

### Post by AlexBaranosky on 2011-11-19
Says that there were no proprietary drivers in use on my machine, then I tried to install hardware drivers and got this message:

> SystemError: installArchives() failed

I'll have to take a look at the Catalyst Control Center, which I'v never heard of.

Crud. I went to use the CCC (admin) as you suggested and received this message:

> There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.

---

### Post by AlexBaranosky on 2011-11-19
So it sounded like this might help:
[http://ubuntuforums.org/showpost.php?p=9192700&postcount=27](http://ubuntuforums.org/showpost.php?p=9192700&postcount=27)

I tried uninstalling those packages and rebooting, and now when I install hardware drivers I get this message:

> SystemError: E:Unable to correct problems, you have held broken packages.

:confused:

---

### Post by AlexBaranosky on 2011-11-19
*bump*

---

### Post by 4Orbs on 2011-11-19
The Catalyst Control Center is installed automatically when you activate the proprietary driver. If you clicked on the "Activate" button and waited for the driver installation to complete, you should have seen a notification that the system must be rebooted in order for the new driver to work correctly.

After rebooting the computer, you should find the Catalyst Control Center link located in your system menu or maybe the settings menu. Now, since you are getting the error of broken packages... my guess is that you either didn't reboot after the driver installation, or you didn't wait for the installation to finish (sometimes it takes a few minutes or more for the driver to download and install).

---

### Post by HermanAB on 2011-11-19
Could be a broken cable.

---

### Post by AlexBaranosky on 2011-11-20
So when I go to Synaptic Package Manager and check my status, it says I have 0 broken packages, yet if I try to install my drivers it still gives me the error "you have held broken packages" argggh  what should I do next?

---

### Post by 4Orbs on 2011-11-20
If I'm understanding the sequence of events, the most recent thing you've done is to try "Hardware Drivers" and get an error. But just before that, you had already used Synaptic to install fglrx? If that's the case, then Synaptic still shows fglrx as installed?

---

