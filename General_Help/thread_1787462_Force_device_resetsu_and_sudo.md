---
title: "Force device reset\su and sudo"
date: 2011-06-21
forum: General Help
---

### Post by ImTheBatman on 2011-06-21
Hello fellow linuxers,
I've been using Ubuntu for a few months now and I have two questions that bug me:

The first is regarding a Microsoft wireless USB mouse I own (Explorer BlueTrack). Whenever I use Windows and then restart and boot from Ubuntu, my scrollwheel is 5 times faster. Out of tests I have conducted some time ago I know the problem is not software-based, the mouse actually sends the "wheel scrolled" message 5 times for each scrolling. When I physically disconnect and reconnect the wireless transceiver, the problem is solved until the next time I boot from Windows. 

I have been told it is a firmware issue - Windows uploads Microsoft's firmware to the mouse at boot time, which is configured to send 5 scrolling messages. Because my motherboard has On\Off Charge, USB power is constantly on and the mouse retains its firmware. Linux does not upload new firmware to devices at boot time, which is why only a reconnection solves the issue. My question - how can I make Ubuntu restart my USB mouse (or all USB devices) automatically at boot?

Second thing is regarding su and sudo. When I use "sudo <command>" I enter my password and gain root access, everything is fine. When I try to use my password with the "su" command however, I get "su: Authentication failure". I have seen the same issue on numerous other Ubuntu machines. Is there a difference between su and sudo or am I using it incorrectly?

Thanks,
The Batman

---

### Post by coffeecat on 2011-06-21
The first firmware issue. Rather than doing a warm reboot into Ubuntu, try shutting down from Windows, waiting a few seconds and then doing a cold boot into Ubuntu. This sometimes helps with faulty firmware loading issues with wireless cards when going from one OS to another. It might help with your mouse firmware problem.

With regard to sudo/su, typing "su" in the terminal causes the system to prompt for the root password, not yours. The root account is locked by default in Ubuntu, hence the error message. If you want a root terminal, type:

```
sudo -i
```Also, have a read of this. It explains everything:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ImTheBatman on 2011-06-21
The article is great and has indeed solved my problem. Regarding the mouse, the firmware is retained even after powering off the computer for the whole night - I assume this is because of Gigabyte's On\Off Charge feature which supplies power to all USB ports even when the computer is powered off, allowing the transceiver's firmware to be kept. I can disable On\Off Charge from the BIOS menu, but if there's an alternative I'd rather keep it on.

---

