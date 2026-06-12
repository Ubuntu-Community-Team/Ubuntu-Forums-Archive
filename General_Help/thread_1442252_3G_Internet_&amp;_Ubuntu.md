---
title: "3G Internet &amp; Ubuntu"
date: 2010-03-29
forum: General Help
---

### Post by Monotoko on 2010-03-29
Hiya Guys,

I have a netbook for on the move work, and it works great, just a slight problem...its running Windows -.-

Now im trying to get the mobile internet working with Ubuntu on my main laptop, its 10.04 Lucid Lynx Beta 1, if i can get it working il install the netbook remix onto the netbook and use that.

Thinking i would have quite a difficult task ahead of me, i was quite supprised when i saw the option in the connection manager to have a wizard-like setup.

I went through it, choosing UK -> Orange -> Contract...it asked to name the connection and apparantly that was that...i was quite chuffed.

I disconnected from the internet and plugged my USB Modem in, it started flashing blue, which usually means its searching for its network.

Now..the problem is it Ubuntu either doesnt register the modem, or it doesn't realize its my way of connecting through the mobile broadband connection i just set up.

I do not see the connection in the "Available Connections" section...i have gone back to the section in network manager many times and tinkered around, checking "Connect Automatically" but nothing seems to do any good, are there any extra steps i have to take in order to make it work? I thought it could be a module issue so i restarted the computer in hope that it might recognise it, but had no luck.

The modem is a HUAWEI Model-E1752
Thank you for any help.

~Monotoko

---

### Post by waynefoutz on 2010-03-29
Go into Synaptic package manager, see if you have libmbca0 and mobile-broadband-provider-info packages installed.

---

### Post by Monotoko on 2010-03-29
I have the mobile-broadband-provider-info apparently, but when searching synaptic for libmbca0 i get no matching results.

---

### Post by waynefoutz on 2010-03-29
> **Monotoko said:**
> I have the mobile-broadband-provider-info apparently, but when searching synaptic for libmbca0 i get no matching results.

My bad. It seems that package isn't in Karmic. Previous versions, which I'm still using, use that package. I'm not sure what version of it Karmic is using.

---

### Post by Monotoko on 2010-03-29
Hmmm, i cant find anything on Google about the package drop.

But i assume they wouldnt drop an essential connection package if they have
mobile-broadband-provider-info already installed...they must have the library for it, even if it is under another name..right?

---

### Post by waynefoutz on 2010-03-29
I found this:

[http://www.mail-archive.com/ubuntu-desktop@lists.ubuntu.com/msg02149.html]("http://www.mail-archive.com/ubuntu-desktop@lists.ubuntu.com/msg02149.html")

> Net:
 * uploaded new network-manager, network-manager-applet 0.7 snapshot
(final for karmic)
 * uploaded new mobile-broadband-provider-info package
 * work with tony on modemmanager and network-manager/-applet 0.8; NEWed
them, fixed packaging bugs and get it pre-promoted for alpha4
 * libmbca removal from karmic (superseded by NM wizard itself)
 * worked with tony on latest connman updates

I don't know what NM Wizard is...I'm afraid I can't be much help. Ubuntu is the best distro for Mobile Broadband cards and tethering phones. It's usually a simple affair if you are using the Gnome version. Kubuntu with KDE is a completely different animal, much harder to set up. I'm running Intrepid, and those two packages I mentioned are what makes it all work in Intrepid and Jaunty.

---

### Post by Monotoko on 2010-03-29
I think the NM Wizard is the wizard like setup i mentioned in my first post...iv been through that and set it up.

It just doesnt seem to recognise my modem when i plug it in, as i said it looks like its scanning for something (blue light blinks every so often on the modem) but cant seem to find it for whatever reason.

And the connection is never in my "Available Connections"

---

### Post by waynefoutz on 2010-03-29
Did you try this? This guy in Ireland put a guide together for getting it working in 9.10, and yeah, there is a package that needs to be installed. usb_modeswitch, according to his guide. 

[http://blog.simple2web.ie/?p=363]("http://blog.simple2web.ie/?p=363")

It seems the problem is Ubuntu is trying to load the SIM card as a USB storage device.

---

### Post by Monotoko on 2010-03-29
It worked!

Thank you very much :)

---

