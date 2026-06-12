---
title: "Kismet + Orinoco_cs, uninstalling programs?"
date: 2009-09-11
forum: General Help
---

### Post by Jungle-Cat on 2009-09-11
Hey,
So I'll make this as short and simple as I can.

(1) I've finally gotten something to install from source correctly, Kismet 2009-06. I installed with **sudo make install, apparently I should have used suidroot - is there anyway to 'change' it without removing it and recompiling and installing?** Not a big issue, but would like to avoid that... compiling on a P3 lappy isn't exactly Usain Bolt stuff.

(2) So I've installed from source, not using apt-get, which is quite an accomplishment from my part since in the long run I'm wanting to use Linux as much as I can. So I need to know, **how can I now uninstall what I installed from source?**. I'm asking generally, not just for Kismet but please do use it as an example. If I wanted to, could I generate a deb binary from what I compiled, so I can store a package and possibly even distribute it? If this isn't as simple as a few commands, I won't bother.

(3) **Kismet does not like the orinoco_cs** that Ubuntu (Xubuntu) has installed. (If it matters - I used netboot.tar.gz files and installed over PXE as I required a nothin' but net install. Then used apt to install xubuntu-desktop) So I need to know, how do I check the version of the orinoco_cs module installed currently? As the newer versions are monitor patched where as older ones need patching. **Is the injection patch the same as the monitor patch?**

After the server starts and uses the 'source' (Capture interface) it says 'detected 'orinoco_cs' driver for interface eth1;This driver will not report packets in rfmon under many firmware versions. Kismet will continue trying to use it, however if you don't see any packets check 'dmesg' and consider changing firmware on your card'.

No packets indeed... I can't use iwconfig to set 'mode monitor' - permission denied or something (did run as root) - however airmon-ng seamed to put it into monitor just fine. I noticed though, on a different system that I've used Backtrack 4 on, airmon made a new interface, mon0, for monitor mode ot be used on. Not sure of it is differing versions of aircrack-ng (I installed using apt). I belive the issue to be the bad orinoco_cs driver package being old and not properly being patched for monitor mode, but I base that on nothing really. When I use airmon-ng to put the card into mon mode, the green light does stay green though... so it does seam to work.

In Wireshark, with the card in this apparent monitor mode, there are simply no interfaces listed. Not even eth0 (Wired). :S
(Edit: needed to run wireshark as root. Still, no packets being captured. iwconfig reports eth1 as being in monitor mode.)

(4) More a clarification - In linux, drivers are a subset of modules? Ie. all drivers are kernel modules, but not all modules are hardware drivers? Modules such as X etc provide GUI, utilise drivers etc... just a quick explanation on how drivers work (Or a link to a good guide) would be great.

I have a Lucent Orinoco PCMCIA card, and I'm wanting it setup to work nicely with Kismet and aircrack-ng. Possibly a serial attached GPS later on ;) But won't fuss with that now.

I'm using Ubuntu 8.04 LTS with xubuntu-desktop.

Edit: Found modinfo - but it doesn't say the version of orinoco_cs installed. Atleast, not that I can see.

Hope that is clear enough,
Thanks.

Edit:
[http://ubuntuforums.org/showthread.php?t=583426](http://ubuntuforums.org/showthread.php?t=583426)
These errors still seam to exist.
[https://wiki.ubuntu.com/OrinocoMonitorMode](https://wiki.ubuntu.com/OrinocoMonitorMode)
Step 4 does not work - just get file not found errors (hundreds of them - file is there about about 40mb)

I've discovered that Backtrack 4 is debian/ubuntu based, but on ubuntu 8.10. Anyway I can dl deb packages from there and use in my 8.04 LTS distro? Just stuff like aircrack which I feel will be bleeding edge there rather than coagulated hammer here ;)

---

### Post by Jungle-Cat on 2009-09-11
And-a-bump.

---

### Post by pieces84 on 2010-06-08
Hi Jungle-Cat,
 
I'm a newbie..
Could you please help me on how to install orinoco_cs on ubuntu?

---

