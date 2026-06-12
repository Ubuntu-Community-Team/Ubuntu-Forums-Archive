---
title: "Problem with DHCP system..."
date: 2006-03-01
forum: General Help
---

### Post by unholy_dude on 2006-03-01
I have Ubuntu Breezy 5.10, but I can't access to internet in no way... I've tried automatic DHCP connection, but it still won't work, as it says it is active.

So, I need some advices; how can I acces to internet?

I have integrated Intel Corp. Pro 100mb -ethernet card.
Ubuntu recognises it, BUT IT JUST WON'T WORK!

Pls help!

---

### Post by Ramses de Norre on 2006-03-01
What error messages gives it? Or what makes you think it doesn't work?
A little more info would be useful.

Static IP always worked better for me. Just fill in the numbers, make sure your dns servers are configured too.

---

### Post by unholy_dude on 2006-03-01
[QUOTE=Ramses de Norre]What error messages gives it? Or what makes you think it doesn't work?
A little more info would be useful.

Static IP always worked better for me. Just fill in the numbers, make sure your dns servers are configured too.[/QUOTE]
It won't give ANY errors, except on installation.. It says that "could not make automatic connection" or smthng...
In Ubuntu-Desktop it won't say nothing, just loads a while, then shows that it is active, but FireFox can't still find any hosts or websites. Same goes when I try to ping other hosts and websites (connection refused or smthng).

I'm just so pissed off 'coz this...

With Windows XP pro all network things worked perfectly, but not with ubuntu.
Friend says that it won't support some integrated ethernet cards... :cry: 
Not really sure about that, though...

---

### Post by ttread on 2006-03-01
Try opening a console and type

ifconfig

to see your network interfaces.  If your card appears but is not getting an ip address, try typing

sudo dhclient eth0
(if your network card is different from eth0, then substitute)

It will broadcast a DHCP request and you can see what response (if any) is returned.

-Ted

---

