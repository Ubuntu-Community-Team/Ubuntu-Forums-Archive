---
title: "Net no longer connects within VM (W7 host)"
date: 2010-09-18
forum: General Help
---

### Post by jrowland on 2010-09-18
I've been running an Ubuntu VM (10.04 LTS) on my Win7 (Home Premium 64bit) desktop successfully for several months now using VMPlayer (v3.1.1).  My problem began when I booted up the VM today - my wife decided to reboot the PC without gracefully closing down my applications when Windows told her that she needed to reboot to complete security updates.

When I booted up the VM, the Ubuntu desktop went right back to the exact same state that it was in before the host reboot - the same programs were open, I didn't need to log in, etc.  However... I now have no networking.  The network icon (NetworkManager Applet 0.8) shows the red exclamation point.  If I click on Auto eth0, it attempts to connect for a bit, and then says "offline".

My VMware Player settings for this VM are configured for bridged networking, and the "network adapter" icon shows online.  If I go into the VMWare Player settings and change the networking to NAT, and then click on Auto eth0 again, the networking comes online.  However, I don't want NAT - I want this Ubuntu client exposed to my network with it's own IP address.

At this point, I'm really not sure if the problem is within Ubuntu or within VMWare Player, or something on my Win7 host.  I have zero skill at troubleshooting within Ubuntu - still fairly new to the linux scene.  My Windows firewall is turned off. DHCP is enabled on my network, and the router is available.

Any ideas on how I might further troubleshoot this problem?

---

### Post by dcstar on 2010-09-19
> **jrowland said:**
> I've been running an Ubuntu VM (10.04 LTS) on my Win7 (Home Premium 64bit) desktop successfully for several months now using VMPlayer (v3.1.1).  My problem began when I booted up the VM today - my wife decided to reboot the PC without gracefully closing down my applications when Windows told her that she needed to reboot to complete security updates.
.............

Any ideas on how I might further troubleshoot this problem?

Please ask VM questions in the Virtualization forum.

---

