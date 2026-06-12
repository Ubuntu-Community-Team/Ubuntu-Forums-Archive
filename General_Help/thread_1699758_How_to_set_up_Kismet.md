---
title: "How to set up Kismet"
date: 2011-03-04
forum: General Help
---

### Post by FGm496 on 2011-03-04
I'm trying to set up Kismet for my computer but can't figure out how to configure it properly.
I have the Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller.
So what patch do i need, and how do i set up the source?
Like source name, packet capture source, etc....

---

### Post by vivek.pandey on 2011-03-04
have you downloaded kismet?

---

### Post by FGm496 on 2011-03-04
> **neo_aryan said:**
> have you downloaded kismet?

...yes I have kismet downloaded.....

---

### Post by vivek.pandey on 2011-03-04
> **FGm496 said:**
> ...yes I have kismet downloaded.....

it actually needs sudo to work so did you try sudo kismet on terminal?

---

### Post by FGm496 on 2011-03-04
> **neo_aryan said:**
> it actually needs sudo to work so did you try sudo kismet on terminal?

It's no problem with the actual use of the program itself. It's the config file. I can't get the settings right. Or even the patch for kismet to recognize my WiFi card.

---

### Post by CVGH on 2011-04-03
Hi,

Thought I'd give Kismet a tumble.
According the the website, kismet does configuration when you first start it?

Ran kismet as sudo:

```
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.
```I've got a Intel wireless chip [ipw2200 is being used] on eth1.
Do I edit kismet.conf in etc/kismet?

I'm running from a USB install BTW....

Thanks!

Added sources=ipw2200.eth1,addme to kismet.conf

---

