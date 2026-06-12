---
title: "broadcom b43 wont activate"
date: 2009-08-12
forum: General Help
---

### Post by MistaMista on 2009-08-12
im tryin to get my wireless card to work and this driver wont activate

---

### Post by MistaMista on 2009-08-12
also i try to run this commnd sudo apt get update and it says it failed to fetch and couple of sites.....is this because of no internet connection

---

### Post by fluffman86 on 2009-08-12
You'll probably need to download the driver for the broadcom.  Ubuntu will do this automatically once you have internet connection, meaning you'll need to plug up with an ethernet cable for a little while to get the rest of your drivers.

If Ubuntu doesn't let you know you have restricted drivers available, then you can ask to check once you're online by going to System > Administration > Hardware Drivers.

---

### Post by overdrank on 2009-08-12
> **MistaMista said:**
> im tryin to get my wireless card to work and this driver wont activate

Hi and welcome, You will need a Internet connection to enable the drivers under hardware drivers. :)

---

### Post by MistaMista on 2009-08-12
when i plug in my wired connection ubuntu doest see the connection

---

### Post by fluffman86 on 2009-08-12
Check the cables and connection with another computer.

---

### Post by MistaMista on 2009-08-12
it works on my other laptop....

---

### Post by overdrank on 2009-08-12
> **MistaMista said:**
> it works on my other laptop....

Ok identify your hardware. You can use the command ```
lspci
``` in the terminal located under applications, accessories. 
Then use this command ```
iwconfig

``` for the wlan. I am not great with networking but this info will help and other may pitch in. :)

---

### Post by fluffman86 on 2009-08-12
maybe your ethernet port is dead.  Try installing the b43-fwcutter package/driver manually.

[http://ubuntuforums.org/showthread.php?t=763995](http://ubuntuforums.org/showthread.php?t=763995)
^ that should help.

---

