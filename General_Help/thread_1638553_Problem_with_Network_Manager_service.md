---
title: "Problem with Network Manager service"
date: 2010-12-05
forum: General Help
---

### Post by Red_Steve on 2010-12-05
So... I used this tutorial [https://wiki.ubuntu.com/ConnMan/Installation](https://wiki.ubuntu.com/ConnMan/Installation) to test out indicator-network but now I want to switch back to network manager

The Problem is: I had it uninstalled and deleted the files /etc/init/network-manager.conf & /etc/xdg/autostart/nm-applet.desktop 

Now, if I disable indicator-network and reenable network-manager and nm-applet, nm-applet says "no networking devices available"

I think it's related to the fact that something in network-manager.conf is missing which I should switch back. Any advice on how I could repair network manager?

---

### Post by dcstar on 2010-12-06
> **Red_Steve said:**
> So... I used this tutorial [https://wiki.ubuntu.com/ConnMan/Installation](https://wiki.ubuntu.com/ConnMan/Installation) to test out indicator-network but now I want to switch back to network manager

The Problem is: I had it uninstalled and deleted the files /etc/init/network-manager.conf & /etc/xdg/autostart/nm-applet.desktop 

Now, if I disable indicator-network and reenable network-manager and nm-applet, nm-applet says "no networking devices available"

I think it's related to the fact that something in network-manager.conf is missing which I should switch back. Any advice on how I could repair network manager?

So you **deleted** the files that the HOWTO **specifically said to move** so they could be restored later, and now it isn't working?, perhaps a reinstall of Ubuntu may get the message through to actually follow the instructions in these things.

---

### Post by Red_Steve on 2010-12-06
> **dcstar said:**
> So you **deleted** the files that the HOWTO **specifically said to move** so they could be restored later, and now it isn't working?, perhaps a reinstall of Ubuntu may get the message through to actually follow the instructions in these things.

Please have the text reread. It advises to completely remove this renamed files in the case you will fully migrate to connman as Network Manager is then completely useless. But now I want to migrate BACK and all I can see is that besides only removing the packages network-manager and network-manager-gnome (and NOT purging them) these files seemingly don't get recreated as Network Manager is unable to control network devices.

I've found a bug with a possible solution where connman and network manager are conflicting packages and uninstalling the first would solve it but once done my network completely vanished and I had to manually specify my ethernet uplink by editing /etc/network/interfaces as Network Manager still was unwilling to control my devices. I'm now back on connman and everything works but this is a bummer.

Edit: I solved it by simple copying the missing files from my live cd and then uninstalling connman.

---

