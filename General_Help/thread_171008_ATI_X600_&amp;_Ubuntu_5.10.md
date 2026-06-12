---
title: "ATI X600 &amp; Ubuntu 5.10"
date: 2006-05-05
forum: General Help
---

### Post by weblife23 on 2006-05-05
Ive only just installed Breezy Badger and am now trying to get X working with my ATI Radeon X600. According to the guide at [https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI](https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI) I need to run the following commands...

1. sudo apt-get install linux-686
2. sudo apt-get install xorg-driver-fglrx
3. echo fglrx | sudo tee -a /etc/modules
4. sudo dpkg-reconfigure xserver-xorg

...and then restart. Ignoring the fact that I dont really know what any of that does, I can get past the first command. I tried running at from / but get a message saying cant find the package linux-686. For command 2 I get a message saying it cant find xorg-driver-fglrx.

Im a newbie, so this may be a really simple problem, but please help me out if you can. Thanks alot!

---

### Post by louis_nichols on 2006-05-05
What you need to do is enable all the repositories for packages. [Here]("http://www.ubuntu.com/ubuntu/components") and [here]("https://wiki.ubuntulinux.org/Repositories?highlight=%28repositories%29") you can find out why this is, and [here]("https://wiki.ubuntulinux.org/AddingRepositoriesHowto?highlight=%28repositories%29") is how to do it.

Good luck!

PS: [This page]("https://wiki.ubuntulinux.org/AptGetHowto") should make you understand what those commands are and what they do.

---

### Post by weblife23 on 2006-05-06
[QUOTE=louis_nichols]What you need to do is enable all the repositories for packages. [Here]("http://www.ubuntu.com/ubuntu/components") and [here]("https://wiki.ubuntulinux.org/Repositories?highlight=%28repositories%29") you can find out why this is, and [here]("https://wiki.ubuntulinux.org/AddingRepositoriesHowto?highlight=%28repositories%29") is how to do it.

Good luck!

PS: [This page]("https://wiki.ubuntulinux.org/AptGetHowto") should make you understand what those commands are and what they do.[/QUOTE]


Okay, I think I get the general idea of these packages, but do I need to be connected to the net to say run this command...

sudo apt-get install linux-686

If so, how do I set that up? I have an ISP-specific ADSL modem plugged into USB, with a Windows driver CD-ROM. Where do I start setting that up on Ubuntu - that is of course, if I need to!

Thanks again

---

### Post by Ramses de Norre on 2006-05-06
You're X isn't working yet? Then you'll need to get that up with vesa drivers because getting a usb modem to work could be a little tricky (and you don't want to do that from console only I think).
Go into a tty (ctrl-alt-F1) and do ```
cd /etc/X11/
sudo cp -p xorg.conf xorg.conf.bak
sudo vi xorg.conf
```
Search the device section (with something about ati x600) and change the driver (which is currently set to ati I assume) to vesa.
Then press esc, shift-q and type wq and enter.
Then do ```
sudo /etc/init.d/gdm restart
```
And press ctrl-alt-F7 if you don't get a login screen automaticaly.
You should be able to log in but don't expect nice graphics from vesa.
You can start searching for setting up the modem and when that's acomplished you can install the fglrx drivers.

---

### Post by weblife23 on 2006-05-06
[QUOTE=Ramses de Norre]You're X isn't working yet? Then you'll need to get that up with vesa drivers because getting a usb modem to work could be a little tricky (and you don't want to do that from console only I think).
Go into a tty (ctrl-alt-F1) and do ```
cd /etc/X11/
sudo cp -p xorg.conf xorg.conf.bak
sudo vi xorg.conf
```
Search the device section (with something about ati x600) and change the driver (which is currently set to ati I assume) to vesa.
Then press esc, shift-q and type wq and enter.
Then do ```
sudo /etc/init.d/gdm restart
```
And press ctrl-alt-F7 if you don't get a login screen automaticaly.
You should be able to log in but don't expect nice graphics from vesa.
You can start searching for setting up the modem and when that's acomplished you can install the fglrx drivers.[/QUOTE]

Thanks alot man, Ive now got X working with the vesa driver. Ive downloaded the ATI linux drivers installer in Windows and copied it to the desktop in GNOME using a usb key. It needs to be run as a superuser - how do I do this when not in console?

Thanks again!

---

### Post by louis_nichols on 2006-05-06
[QUOTE=weblife23]Thanks alot man, Ive now got X working with the vesa driver. Ive downloaded the ATI linux drivers installer in Windows and copied it to the desktop in GNOME using a usb key. It needs to be run as a superuser - how do I do this when not in console?

Thanks again![/QUOTE]

The best thing is to open a terminal: Applications/Accessories/Terminal

Then just use the usual sudo <command name>

You could just set nautilus for example to run it at double click, but you'll need the command line feedback anyway.

Still.. the best way is to instll the drivers in the repos. Jyst open System>Administration>Synaptic package manager and do a search for fglrx and you'll find the drivers there. I believe they are the latest.

---

### Post by Ramses de Norre on 2006-05-06
The ati driver needs to be reinstalled with every kernel upgrade, the version from the repos does this automaticaly. But you definitely need internet acces for it because the package has a lot of dependencies. I'd get the internet working first and then install the drivers.

---

### Post by weblife23 on 2006-05-06
[QUOTE=Ramses de Norre]The ati driver needs to be reinstalled with every kernel upgrade, the version from the repos does this automaticaly. But you definitely need internet acces for it because the package has a lot of dependencies. I'd get the internet working first and then install the drivers.[/QUOTE]

I connect to my ISP through an USB ADSL modem. The device manager does show an ADSL modem, but I wouldnt have a clue where to start to set it up to connect to my ISP! With Windows I just installed some software sent to me by my ISP and it all worked. 

Where do I begin!?

And PS. Why is everything so damn hard setting up Linux? How is it ever going to get wide acceptance this way?

---

### Post by Ramses de Norre on 2006-05-06
You can't blame Linux for that, the problem is with the manufacturers not providing native drivers and support for Linux.
But the more people using Linux and complaining about this, the more manufacturers will suport Linux too.
So if you want to do something about it: start complaining to the hardware manufacturers, isp's who doesn't support Linux etc.

And I don't know how to get that usb modem working, I'd search the forums and google and if you don't find a clue start a new thread for it.

---

### Post by djsamsel on 2006-05-06
it'll be a long time before linux recieves what you are calling wide acceptance (which by you're standards is the same as what window's offers as plug and pray). linux is much more difficult to configure with non-standard hardware and an usb adsl modem is non-standard. i would guess your modem has the choice of usb or ethernet and i think you will find it much easier if you connect to it by ethernet.  your computer probably has an etherney jack and ubuntu probably installed a driver for it. configuring dhcp will be much easier than tryng to do it through a usb port.:p

---

### Post by deathshadow on 2006-05-06
[QUOTE=Ramses de Norre]You can't blame Linux for that, the problem is with the manufacturers not providing native drivers and support for Linux.
[/QUOTE]
I wouldn't go that far - a lot of manufacturers aren't providing native drivers because Linus has yet to set a fixed interface between the kernel and the hardware... To write a device driver for linux you end up spending more time just coding in the differences between the kernels than you do actually interfacing the device! There's a reason why if you go to some companies sites they'll have rpms or .tar.gz that only target an EXACT kernel build, and if you vary from that it doesn't work.

Linux is a great tool, but let's be honest about it's shortcomings - like lack of binary level compatability *(I know the gentoo nuts would argue the need for that, this isn't a gentoo forum and most of us don't compile our entire OS from scratch)*, unpredictability of kernel versions on the driver codebase *(HOW many devices got 'left out' in the cold by the 2.6 kernel again?)* and the lack of financial support to actually PAY someone to fix EVERYTHING instead of 'hoping' somebody picks up the odds and ends that aren't getting coder support from companies like Red Hat and IBM.

Sometimes there are advantages to Windows - like having a device interface to the OS (WDM) that hasn't seen a REAL change in functionality or binary level compatability since NT4.

But then there are the disadvantages - like not having seen a major revision since NT4.

Still, a FIXED api for going between device drivers and the kernel? Is that REALLY too much to ask? (Linus says yes, it is.)

---

