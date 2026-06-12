---
title: "Sound, hotplug failing after upgrade"
date: 2006-06-10
forum: General Help
---

### Post by MSatterwhite on 2006-06-10
Yesterday, I upgraded from Breezy to Dapper using dist-upgrade. After the upgrade, my sound doesn't work (I have a Soundblaster Live) and I  don't have access to my USB devices. I don't have any idea where to start on correcting this.

Can someon offer me some direction? Right now, I'm looking at reinstalling Breezy.

tia
---Michael

---

### Post by pestie on 2006-06-10
I had the exact same problem. I just upgraded to Dapper and found several odd things:
[LIST]
[*]My PCMCIA wi-fi card didn't configure itself with DHCP when I plugged it in
[*]My sound card's low-level drivers were not getting auto-loaded
[*]Upon attempting to start OpenVPN, the tun.ko kernel driver wasn't being loaded and /dev/net/tun was not auto-created when I loaded tun.ko by hand
[/LIST]
These are all things related to the hotplug subsystem, I believe. I know very little about hotplug and/or udev, but I figured maybe a reinstall of that system would fix the problem. So I tried searching for it, and *hotplug is missing from the apt repositories*. The "hotplug" package exists in the repositories and is installed on my Breezy systems, but it's nowhere to be found on Dapper. Yeah, uh, that's a *problem*, isn't it? Unless it's been superceded by something else, there's a serious issue here.

---

