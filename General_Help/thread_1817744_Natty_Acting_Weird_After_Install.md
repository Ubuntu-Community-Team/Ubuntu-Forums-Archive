---
title: "Natty Acting Weird After Install"
date: 2011-08-03
forum: General Help
---

### Post by Dan Again on 2011-08-03
I wiped my hard drive and did a fresh install of Windows 7 followed by a fresh install of Natty using the guide I found here...

[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)

Now I'm experiencing some problems...

[LIST]
[*]wireless isn't working (okay, this seems pretty normal)
[*]when I try to open gnome-system-monitor nothing happens
[*]when I try to access File System my system hangs
[/LIST]

Any idea what the root of these problems are and how I can address it/them?

Thanks!

---

### Post by Dan Again on 2011-08-03
So actually it's not just trying to access the File System that causes Nautilus to freeze. Nautilus just freezes a lot.

---

### Post by Dan Again on 2011-08-04
Bump.

Anyone? Please?

---

### Post by Blasphemist on 2011-08-04
Sorry to hear you're having trouble. Let me ask some basics first please.

When you boot does the hard drive quit being active pretty quick? Does boot happen as quickly as normal?

One of the first thing I do after an install is software updates. Did that go normally? Are any updates still pending or is everything up to date?

Which environment are you running? Classic? Does your hardware not support Unity? And while I'm thinking about video, do any additional drivers show up? That could explain the wireless issue too.

Have you reviewed your logs? This is too often overlooked. This may lead you to questions but can be a big help.

Is windows working well? If there is a hardware issue it would likely show up to some degree in windows too.

What have you done working on the wireless issue?

Please run this utility.
```
sudo lshw
```
Without a parameter this will produce a good bit of info but without knowing what to point at that is good. Please post the results within code tags. If lshw isn't installed it will tell you how to make it so.

---

### Post by Dan Again on 2011-08-04
Jim! Thank you! Switching to classic solved all the really "weird" problems - Nautilus is working great, can access gnome-system-monitor, etc. This is no problem for me at all because I don't like using Unity...just hadn't taken the extra second to change the Ubuntu theme.

Trying to figure out the wireless issue now. To answer your questions...

Boot is pretty quick. After I enter my password at login it seems a little laggy, but nothing too serious.

Haven't been able to install updates...no internet.

You now know the environment that I'm running. Additional drivers did show up, but I wasn't able to download them...no internet.

I've reviewed some logs, but am not advanced enough to really understand them.

Windows works fine...wireless and all.

So far on the wireless issue I have gone in to a wireless config file and blacklisted some drivers or something. I got those instructions on another post from this forum, but can't find it now.

Do you still need the output from that utility, or was that more for the system issues than the wireless issues? I can give you that output, it's just kind of hassle since the computer in question doesn't have internet.

Gonna keep working on this, but if you've got any ideas on how to fix the wireless issue or which logs I need to be looking at I would really appreciate that. Thank you so much for the help you've given me so far!

---

### Post by Dan Again on 2011-08-04
Okay, so I'm still having some of the "weird" problems...even with Classic environment. Nautilus hangs when I try to access /. Won't open Synaptic. System Monitor still opening fine, though. Still no wireless access. Argh.

---

### Post by Blasphemist on 2011-08-04
It sounds like the place to start is getting the ability to get to the internet and do updates. What wireless adapter do you have? Are you able to get wired to the net? Can you run this and see what it shows for your wireless now?
```
sudo lspci -v
```
Look for the section like mine that follows.
> Network controller: Intel Corporation WiFi Link 5100
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at d4600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-22-fa-ff-ff-dd-f7-08
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn


---

### Post by Dan Again on 2011-08-04
Hi, Jim. I am using a D-Link external adapter. At the moment I am not able to get onto the web with a wire, but I can make that happen, albeit with some difficulty...would just require a bunch of moving stuff around and would be a hassle.

So I'm not able to run any command prefaced by sudo. For instance, I type "nautilus" in a terminal and a nautilus window pops up - if I try to do much of anything with it the window freezes, but a window pops up nonetheless. Type "sudo nautilus" and the terminal hangs. Same story with lspci. When I run lspci without sudo I get some output, but it does not show a wireless device, which is funny because my system is seeing wireless networks and attempting to connect to them but failing to do so and repeatedly asking for my password.

---

### Post by Dan Again on 2011-08-04
Bump. Does anyone else have any ideas?

---

### Post by Dan Again on 2011-08-05
Bump. Suggestions?

---

### Post by btindie on 2011-08-05
I think I had problems with Natty when I originally installed it, it wasn't until I'd updated it that it started to behave correctly - or it may have been an update that fixed a previous update? Anyhow ...

Your best bet is to get an internet connection sorted so you can perform the update, it's more likely to just work if you use a wired connection as opposed to a wireless one.

If you type
```
ls /sys/class/net
```is there a wlan0 listed? Or anything other than lo or eth0 ?? If there isn't, then it hasn't got the ability to use your wireless.

Have you tried using a live cd in that machine, did the wireless work then??

You could always try doing an [offline upgrade]("https://help.ubuntu.com/community/InstallingSoftware#Use%20apt-offline") though it's probably more hassle than trying to connect it via a wired connection.

---

### Post by Dan Again on 2011-08-14
Thanks to everyone for their help on this and sorry it's taken me so long to get back to this situation...Summer session just ended and I finally had the time/energy to deal with it.

I pulled the computer into the room with my router and hooked it up with a wired internet connection, performed updates and installed additional drivers. Works like a dream now - no problems whatsoever.

Thanks again, everyone!

---

