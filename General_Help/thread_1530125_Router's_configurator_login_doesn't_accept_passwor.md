---
title: "Router's configurator login doesn't accept password"
date: 2010-07-13
forum: General Help
---

### Post by norm.h on 2010-07-13
I have a ZyXEL Wireless ADSL Modem Router, an Ethernet connected desktop, and a wireless  laptop.
Both machines run Ubuntu 10.04 fully updated, and Firefox 3.6.6 with identical preferences.
The Epiphany browser is also installed on both machines, and Java 6 is on the desktop only.

When I put 192.168.1.1 into the address bar on either machine, it takes me to the router's web-based configurator login page, but only the wireless laptop will accept my  password.
If I connect the laptop via Ethernet, it won't accept my password. 
This is the same using either browser.

Enabling / disabling pop-ups in Firefox, and / or AdBlock Plus, makes no difference, and I don't have this problem with other sites that require a password.

This a recent issue, about a week old.
Everything worked properly before then, and I've not changed or installed anything recently, except the usual Ubuntu recommended updates.

---

### Post by AceRoom on 2010-07-13
What exactly do you get when you type the address when on Ethernet on your laptop?

The page works from your desktop on Ethernet?

---

### Post by norm.h on 2010-07-13
> **AceRoom said:**
> What exactly do you get when you type the address when on Ethernet on your laptop?

The page works from your desktop on Ethernet?

When either machine is on Ethernet, typing the address 192.168.1.1 takes me to the router configuration login page. When I attempt to login, my password isn't accepted.

No, the page only works for laptop wireless.
BTW, the desktop isn't wireless enabled.

---

### Post by scottuss on 2010-07-13
What happens if you try to ping stuff (i.e the router itself, and maybe Google or another public site)? via ethernet on either the laptop or desktop.

---

### Post by theozzlives on 2010-07-13
you could reboot the router by unplugging it for 5 seconds and plugging it back in. Alternatively you could try the reset button and put it to factory defaults, you would have to setup your wireless, port forwarding and DHCP again.

---

### Post by tarps87 on 2010-07-13
It sounds like wired admin access has been disabled on the router, this is possible on some routers and yours may be one. Try having a look through the routers settings

---

### Post by scottuss on 2010-07-13
> **tarps87 said:**
> It sounds like wired admin access has been disabled on the router, this is possible on some routers and yours may be one. Try having a look through the routers settings

Sounds plausible

---

### Post by norm.h on 2010-07-13
> **tarps87 said:**
> It sounds like wired admin access has been disabled on the router, this is possible on some routers and yours may be one. Try having a look through the routers settings

Can't find anything relating to this.

Everything else is working as it should.

Looks like I'm into a factory reset.

---

### Post by philinux on 2010-07-13
Enable cookies on the machine that wont accept the password. ;)

---

### Post by scottuss on 2010-07-13
> **philinux said:**
> Enable cookies on the machine that wont accept the password. ;)

From what I can tell from the OP, it works on Wireless on the laptop but not wired on the laptop, that would suggest it has nothing to do with cookies.

---

### Post by norm.h on 2010-07-13
> **philinux said:**
> Enable cookies on the machine that wont accept the password. ;)

Cookies have always been enabled

---

