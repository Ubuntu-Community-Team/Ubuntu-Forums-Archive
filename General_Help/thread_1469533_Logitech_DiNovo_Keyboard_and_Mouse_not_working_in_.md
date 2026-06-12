---
title: "Logitech DiNovo Keyboard and Mouse not working in 10.04"
date: 2010-05-02
forum: General Help
---

### Post by GaussBonnet on 2010-05-02
Hi all!

I've just upgraded from karmic to 10.04. After rebooting my system everything seems to work fine except my mouse and keyboard are not working.

Stupid of me to upgrade now since i have a report due for tomorrow and now i have no way of getting in to the system. :confused:

Can anybody help me resolve this issue?

---

### Post by dino99 on 2010-05-02
you should be able to boot and open a terminal:

sudo apt-get install gconf-editor

use it and answer "yes" when asked

install : logitech-applet

sudo dpkg-reconfigure bluez

sudo dpkg --configure -a

sudo apt-get install -f

maybe some usefull help here: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/269851](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/269851)

---

### Post by GaussBonnet on 2010-05-02
Thank you for your advice! :)

How do i get into a terminal without a working keyboard or mouse? I've tried booting the different alternatives in GRUB but none of them appears to work.

Is there any way to boot directly into a terminal considering my situation?

---

### Post by GaussBonnet on 2010-05-02
:guitar:

This advice from Kent Wilkinson fixed my problem right away. I had to use the on-screen keyboard and use an old PS2-mouse.

"
                 I had a look at [bug #444420]("https://bugs.launchpad.net/bugs/444420") and came up with a solution,  well at least one that works for me, I changed a line in /lib/udev/rules.d/70-hid2hci.rules
 from
 # Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 to
 KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 I also turned bluetooth off from the icon in the notification bar.
 Hope this helps


"


Many thanks!

---

### Post by efflandt on 2010-05-02
Strange.  Normally my diNovo keyboard/mousepad works totally OS independent (no drivers needed).  I can even enter my BIOS password with it before any OS comes up.  And it worked fine in Karmic without doing anything.  But as soon as the Lucid install CD comes up, no response.

I have not installed Lucid yet, but after seeing this post, tried it with 64-bit install CD from my laptop (so it still has that keyboard/mousepad).  Once the live system came up, there was a Bluetooth applet (which usually does not appear for the proprietary dongle), and initially every time I tried to use the mousepad on the diNovo a popup asked if I wanted to give it access permission.  But it would not give it access, and after I selected to always allow it, the popup no longer came up, but it did not work either.

After editing /lib/udev/rules.d/70-hid2hci.rules from hiddev* to hiddraw*, removing the dongle and reinserting it, the Bluetooth applet was no longer there.  Since I had been playing around with the connect button, I had to press the Connect button on the keyboard and button on the dongle to reestablish a secure Logitech connection between those.  But then the keyboard and mousepad worked fine.  So the Kent Wilkinson suggestion from the bug report should work.

I wonder who broke it, and whether it will be fixed on the 10.04 install isos?  Otherwise it will be a bummer for anyone trying to install it without another wired keyboard/mouse.

PS: I discovered even a simpler solution, just comment out that section of /lib/udev/rules.d/70-hid2hci.rules:

# Logitech devices
#KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]", \
#  RUN+="hid2hci --method=logitech-hid --devpath=%p"

I just tried that from my laptop keyboard on live 10.04 LTS CD, inserted the Bluetooth dongle for my diNovo Edge, and it worked.  Apparently that had been changed from hidraw (which works) to hiddev (which did not work for me) as the result of bug 444420.  But maybe it works best if Linux does not even get involved with it, since to any OS (or BIOS) it should simply appear to be a regular USB hid device.

---

### Post by dino99 on 2010-05-02
> **GaussBonnet said:**
> :guitar:

This advice from Kent Wilkinson fixed my problem right away. I had to use the on-screen keyboard and use an old PS2-mouse.

"
                 I had a look at [bug #444420]("https://bugs.launchpad.net/bugs/444420") and came up with a solution,  well at least one that works for me, I changed a line in /lib/udev/rules.d/70-hid2hci.rules
 from
 # Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 to
 KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 I also turned bluetooth off from the icon in the notification bar.
 Hope this helps


"


Many thanks!

glad you found a work around and put the details here, may help others

---

### Post by Hopey on 2010-05-08
Thanks worked :)

---

### Post by brohmes on 2010-07-22
> **GaussBonnet said:**
> :guitar:

"
                 I had a look at [bug #444420]("https://bugs.launchpad.net/bugs/444420") and came up with a solution,  well at least one that works for me, I changed a line in /lib/udev/rules.d/70-hid2hci.rules
 from
 # Logitech devices
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 to
 KERNEL=="hidraw*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345abce]|c71[34bc]",  \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"
 I also turned bluetooth off from the icon in the notification bar.
 Hope this helps


"


Many thanks!


This worked for me for a while.  But I find that the issue continues to recur.  A restart solves the problem, but it's annoying having to do that every couple weeks or so.  The .rules file still contains the "hidraw*" substitution, but my dinovo edge does not work at all until I reboot.

Any ideas?

---

### Post by outleradam on 2010-09-01
You are having a issue with bluetooth.  I found the quick solution was to unplug and plug back in my dongle.   It would do that randomly on restart, but replugging in the bluetooth dongle always fixed it.

---

### Post by brohmes on 2010-09-03
I've tried unplugging the dongle, with no luck.  Unless I'm just not giving it enough time to reconfigure itself or whatever.

Rebooting isn't the end of the world. This is an XBMC build and I only rarely need to use the mouse/keyboard.

How often does the issue recur for you?

---

