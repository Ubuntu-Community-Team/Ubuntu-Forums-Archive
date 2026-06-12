---
title: "Port 4001 held open by squid proxy"
date: 2011-12-11
forum: General Help
---

### Post by lonewolf88 on 2011-12-11
Running Zenmap, shows 

"4001/tcp open  http-proxy Squid webproxy"

I need that port for another service.

Not using squid, so I did a complete removal in Synaptic and rebooted.

Zenmap still gave the same above results.

Question is, how can I close that port so that it is available to the other service?

(Also, if anyone knows how to open Zenmap from a menu as administrator, I would be obliged for this information.)

As usual, thanks in advance.

---

### Post by zero2xiii on 2011-12-11
Hay,

If you understand the risks of running a program as admin/root, you can do that by appending "gksudo" to the command. Right click the Menu and Clickk on edit menu, then navigate to the program launcher and dubble click, append gksudo to the command.

As far as closing the port goes, why do you need to close it for another program to open it? That does not make sence. More than one program can use a given port at any time.

Cherz

---

### Post by lonewolf88 on 2011-12-11
> **zero2xiii said:**
> Hay,

If you understand the risks of running a program as admin/root, you can do that by appending "gksudo" to the command. Right click the Menu and Clickk on edit menu, then navigate to the program launcher and dubble click, append gksudo to the command.

As far as closing the port goes, why do you need to close it for another program to open it? That does not make sence. More than one program can use a given port at any time.

Cherz

Thanks, need to close the port as the software I want to use (security sort of stuff) insists on sole access.  Can you guide me here?

Also thanks for the tip in the first para above!

---

