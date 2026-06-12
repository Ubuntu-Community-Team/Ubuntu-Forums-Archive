---
title: "Network connection issue after installing KDE 4"
date: 2010-11-18
forum: General Help
---

### Post by zadirion on 2010-11-18
Hello,

Using Ubuntu 10.10. 
Original installation : GNOME
Internet connection worked fine.

I recently switched to KDE. Here's how:
  - installed kdm package first. After reboot, received blank screen with only a terminal opened
  - realised kubuntu-desktop should have been installed too, so I apt-get installed that
  - rebooted an logged in to KDE 4, everything looked ok. However, internet connection no longer worked. The network connection manager reported that no wire was plugged in. Even though it was.
  - logged off and logged back in to the GNOME desktop manager, still no joy.

Any help here please?

Thank you!
Eddie

---

### Post by Kljuka on 2010-11-18
Try (in terminal)
```
ifconfig
```And the interface that should be connected to network (use instead of eth0):
```
ifconfig eth0 down
ifconfig eth0 up
```Maybe your interface starts after this.

---

### Post by zadirion on 2010-11-18
Didn't work.

I looked in dmesg's output and found this:
```

[   10.933762] r8169 0000:04:00.0: eth0: link down
[   10.934015] ADDRCONF(NETDEV_UP): eth0: link is not ready

```
I assume this occured during boot. There is no "the link becomes ready" line in the dmesg, so I assume it never becomes ready, thus my problem.

The same error appears in dmesg's log after "ifconfig eth0 up".
Any ideas what I could try?

Thanks

---

### Post by zadirion on 2010-11-18
Perhaps the issue is simpler than that.
Let's put it in other words shall we:
when I boot in KDE, my network manager sais:

Network Interface:
Cable Unplugged

ifconfig displays eth0, but with no IP assigned.
my network card doesnt have its LED on when the cable is plugged in.
The cable is fine, I tested it with my laptop and it  works perfectly. My network card can't be the issue either, because it worked before switching to KDE.

Any more suggestions on how to troubleshoot this please? I'm getting pretty desperate here :(

Thanks

---

### Post by Kljuka on 2010-11-18
I would suspect that your computer doesn't get IP address from DCHP server. You should check if your computer is configured to obtain IP automatically (that it is not set statically) and that your DHCP server (probably your router) in working correctly.

It might be also something else.

---

### Post by zadirion on 2010-11-19
the  dhcp is not the issue, neither the router, my laptop connects fine. the green led is turned off even if I have the network cable plugged in.
Is there any chance this can be ok and not indicating that the card is broken? It's hard to imagine and understand why it worked just fine before switching to KDE, then just stopped working.

Regards,

---

### Post by SeijiSensei on 2010-11-19
Right-click on the network icon in the tray and choose "Network Management Settings" (or use System Settings > Network Settings to get to the same dialog box). Go to the wired tab and choose Add.  Check "connect automatically" and make any other changes you need to the default settings.  Save your settings, then try connecting again from the network icon.

---

### Post by zadirion on 2010-11-20
Hello,

Thank you for your help. I managed to fix this by downloading kubuntu instead of ubuntu and installing that.

Thanks again!
Eddie

---

