---
title: "usb support on win xp virtualbox"
date: 2009-07-17
forum: General Help
---

### Post by kd0afk on 2009-07-17
I have installed VB and windows xp on a VM. I need to know how to enable usb so that I can sync my ipod touch 2g. In the instructions here [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) it says: [COLOR=Red]"You can now start up Virtualbox, located under **System****Sun Virtualbox** . Create a new machine; the wizard will guide you, the details are outside of the scope for this howto. Within the settings for the machine, ensure both "Enable USB Controller" and "Enable USB 2.0 (EHCI) Controller" are ticked. You can also add a filter to make the iPhone/iTouch automatically pass thru here, otherwise you will have to manually select and enable it when plugged in."[/COLOR] 
 I have looked everywhere and I the only place where I have seen to enable it is in the "devices" settings of the machine and it says "no available devices"
There was no place in the setting up of the VM to enable usb devices.
How do I enable USB support? Itunes is the only reason why I am doing all this, (thanks Steve!!!!!!!!!!!!).
Can someone help on this

Running 
Ubuntu 9.04 Jaunty
VirtualBox 2.1.4

---

### Post by hyperdude111 on 2009-07-17
This guide shows how to enable usb support for virtualbox.

[http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml](http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml)

---

### Post by Entropy_Sam on 2009-07-17
Thanks hyperdude111 - like the OP, I'd like to install iTunes in a VM - that way I can restore my iPod to factory settings if I need to, without tainting my Windows installation with iTunes/QuickTime (which 'hijacks' all your video media by setting itself the default app on installation, without asking permission - especially annoying in FF, as you need to manually re-set all file-type handlers).

---

### Post by kd0afk on 2009-07-17
It didn't work.

---

### Post by PureLoneWolf on 2009-07-17
You need to install the PUEL version from the Virtualbox website, then make sure that your user is a member of the vboxusers group, then logout and back in - At that point the USB should be available.

There is an install guide on the virtualbox website to get the PUEL edition from repositories.

---

### Post by kd0afk on 2009-07-17
So, installing VB from symantic is the wrong version?

---

### Post by maflynn on 2009-07-17
If you downloaded the version via synaptics, it will not have USB support. I went with the version from the website and installed the deb package and everything works as you'd expect (and hope) it would.

---

### Post by lykwydchykyn on 2009-07-17
> **kd0afk said:**
> So, installing VB from symantic is the wrong version?

The one in the default repositories is the open source edition (naturally, since that'd be the one Ubuntu is allowed to distribute).  USB support is found in the non-open-source edition, which PureLoneWolf referred to as the PUEL version (after its license, PUEL, which stands for "Personal Use and Evaluation License").

To install that version, you need to add Sun's repository and then you can find it in Synaptic as "virtualbox-3.0".

Instructions are here: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by uidb4056 on 2009-07-17
> **kd0afk said:**
> So, installing VB from symantic is the wrong version?

You can install from synaptic but before you have to follow this link [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) after the line that says:

_**'Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list:[FONT=monospace]'[/FONT]**_

---

### Post by hibliss on 2009-07-17
Adding the repository from Sun is the best solution, as you will get updates. You can import your current virtual machine image to the full version, it should actually be automatic.

---

### Post by kd0afk on 2009-07-17
I just installed via sudo install but now all I have is VBoxGTK. How do I get back virtualbox.

---

### Post by kd0afk on 2009-07-17
Nevermind. It hided on me.

---

### Post by Skrean on 2009-07-17
I installed VBox using the .deb available for i386 at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


As for using USB Devices in Win XP installed inside VBOX:

The tutorial at [http://linuxchronicles.wordpress.com/2008/05/28/ubuntu-got-usb-in-virtualbox-160/](http://linuxchronicles.wordpress.com/2008/05/28/ubuntu-got-usb-in-virtualbox-160/) worked for me and I have reproduced the relevant instructions below:

[COLOR="Lime"]Add yourself to the group VirtualBox created during install called &#8220;vboxusers&#8221; The VB install creates this group, find it, don&#8217;t add another one.

Create a group named &#8220;usbusers&#8221; and put yourself in it.

sudo groupadd usbusers
sudo gpasswd -a usbusers

Or do the above in Control Center under &#8216;users and groups&#8217;.[/COLOR]

My Group Number for vboxusers was 125. Users and Groups is at System>Administration>Users and Groups.  Click on your username and click Manage Groups on the lower right.

In terminal type

sudo gedit /etc/fstab



type in your password when prompted

In the file that appears paste the following line at the end and save the file...
[COLOR="Lime"]
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0[/COLOR]

If 120 is your number for vboxusers group.

Reboot the computer.

Plug in your USB Devices

[COLOR="Lime"]Open VirtualBox and click on &#8220;Settings&#8221;.

Click on the &#8220;USB&#8221; item in the left pane to edit the USB prefs.

Click on the &#8220;Add device&#8221; button to add a filter and select your printer[/COLOR]/USB Device [COLOR="Lime"]from the list and click on the &#8220;Ok&#8221; button.

Start your VM and Windows should detect your printer.[/COLOR]/USB Device

---

