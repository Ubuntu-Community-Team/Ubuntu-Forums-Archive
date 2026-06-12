---
title: "Installing Speedtouch 330"
date: 2010-05-25
forum: General Help
---

### Post by tufu5 on 2010-05-25
I installed Ubuntu 10.04 this morning and everything is working fine apart from one thing. I am unable to install my Speedtouch 330 modem on it and connect to the internet, I looked on the help pages and found this:

"Visit Ubuntu Packages Search and search for each of the following packages. Download them to a folder that is also visible from Ubuntu (or to a USB stick).

1.python-gtkmozembed
2.python-eggtrayicon
3.python-gtkspell
4.python-gksu2
5.libgdl-1-common
6.libgdl-1-3
7.python-gdl
8.libgda-4.0-common
9.libgda-4.0-4
10.python2.5-minimal
11.libdb4.6
12.python2.5
13.python-gda
14.python-gnome2-extras"

As I cannot access the internet I had to go back to windows, download them onto a memory stick, go back on to Ubuntu and install them. The first 12 worked fine and are now installed but number 13 and 14 wont allow me to update because "the dependency is un-satisfiable" does anyone know what this means and how I can fix it? I was also unable to get the USB ADSL Modem Manager too install either because of another error. Could anyone help please?

---

### Post by szabotihamer on 2010-05-29
I've got the exact same problem. My Speedtouch 330 worked just fine on 9.10, but seems like something it's wrong with the packages. This modem seems to be more and more incompatible with Ubuntu, and seems to be forgotten. Please somebody can help us, it's a big pain to get this device working with 10.04.
Well if not, I'm thinking to buy a new ADSL router and eliminate my old Speedtouch 330. :)
Seems like the USB ADSL Modem Manager hasn't been updated for quite a long time, and the good old UbuDSL too, which was so easy to configure

---

### Post by beyercj on 2010-06-01
Dependency unsatisfiable means that number 13 and 14 depend on other programs hence the long list of programs to download. Try System > Administration > Synaptic Package Manager and enter program name where dependencies are unsatisfiable to find out dependencies and download and install them.

Are you sure you downloaded USB ADSL Modem Manager version 0.5.8? This was the only version which worked for my computer. If it does not work on yours, try a different one.

---

### Post by szabotihamer on 2010-06-02
Thanks for the post beyercj
But I can't access the internet, since the Speedtouch 330 it's the only connection that I have, a really bad ADSL modem. So I can't even access the Synaptic Package Manager. I guess to fix this problem I will need to buy a new ADSL router and send back to hell the Speedtouch 330 from where it came (from my ISP back in 2007)

---

### Post by MichaelSM on 2010-06-22
I had been struggling too, with a Speedtouch 330 v1 USB modem in Lucid.
No luck with either usbadslmodemmanager or Ubudsl (Lucid version).
In the end I downloaded ubudsl_1.0.0.301-1karmic_i386.deb and 
libubudsl-dev_1.0.0.301-1karmic_i386.deb and - ignoring Gdebi's entreaties to use the later versions - installed them in order.(having uninstalled any previous stuff)
After configuring my settings (PPOE in Australia) and filling in the right boxes, I was connected to the Internet via my USB modem.
The only issue I have is that with the Ubudsl applet auto-starting, I sometimes have to right-click on it and hit 'Connect.' Other than that it would appear to be bomb-proof.
Nothing could have been easier once I had the right packages! I live in an isolated area with off-grid and dodgy power supplies which cause problems with mains-powered modems and routers. That's why I like the USB modems.
My laptop boots into either Windows 7, Linux Mint 8, or Ubuntu 10.4. I have USB Modem working in all three OS's.
Happy surfing.
Mike.:popcorn:

---

### Post by TimGS on 2011-02-15
I installed USB ADSL Modem Manager version 0.5.8 via dpkg on the command line. It complained about the lack of python-gnome2-extras, but this didn't stop it being installed and it worked fine.

I believe python-gnome2-extras was a meta-package that just installed various libraries. If those libraries are already there, you will be fine as I was. If not, go to the Jaunty python-gnome2-extras page and you will see a list of packages to install to simulate python-gnome2-extras.

-- Tim.

---

