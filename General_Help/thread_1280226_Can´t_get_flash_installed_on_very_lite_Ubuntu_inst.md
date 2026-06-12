---
title: "Can´t get flash installed on very lite Ubuntu installation?"
date: 2009-10-01
forum: General Help
---

### Post by NintendoTogepi on 2009-10-01
OK, so on this computer I have Ubuntu Lite (basically comes with nothing).

Anyway, I can´t get flash installed. I tried using the tips from here:
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

and it didn´t work. It keeps saying it can´t find the deb or tar.gz. 

Help? Is there something I should install? Right now this has pretty much the following on it:

Firefox
Dillo
AbiWord
XFCE

And thats it.

---

### Post by oldos2er on 2009-10-01
Why not install it from the repos? ```
sudo apt-get update && sudo apt-get install flashplugin-installer
``` This assumes you're using 32-bit Ubuntu.

---

### Post by NintendoTogepi on 2009-10-04
That didn't work...

---

### Post by sendblink23 on 2009-10-04
did you try 

Applications > Add/Remove.. > Show: All available applications > search: flash

Install > *check - Macromedia Flash Plugin > Apply Changes


give that a test... if it doesn't...  you may remove the package in that very same way *Just Un-check it > Apply changes

---

### Post by NintendoTogepi on 2009-11-13
> **oldos2er said:**
> Why not install it from the repos? ```
sudo apt-get update && sudo apt-get install flashplugin-installer
``` This assumes you're using 32-bit Ubuntu.

Just to clarify, this works, and it seemingly downloads fine, but then at the end it says E: Couldn´t find package flashplugin-installer.

I´m not sure how to fix this...

---

### Post by NintendoTogepi on 2009-11-13
I got it installed :)

I just installed and used Synaptic...

---

