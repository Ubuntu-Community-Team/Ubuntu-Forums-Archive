---
title: "Can't start X"
date: 2004-10-23
forum: General Help
---

### Post by 4dSwissCheese on 2004-10-23
Every time I start up, when the login prompt appears, the screen flashes twice and then I get a message saying that it can't start gdm and will disable it until it's fixed.  And then I'm left with just the command line.  My graphics card is a radeon X800SE.  I've tried installing the fglrx drivers, but that doesn't seem to help.  Any suggestions?

(Also, I'm pretty much a complete linux newbie, so could you be as precise as possible in your suggestions?)

---

### Post by NeiL on 2004-10-26
[QUOTE=4dSwissCheese]Every time I start up, when the login prompt appears, the screen flashes twice and then I get a message saying that it can't start gdm and will disable it until it's fixed.  And then I'm left with just the command line.  My graphics card is a radeon X800SE.  I've tried installing the fglrx drivers, but that doesn't seem to help.  Any suggestions?

(Also, I'm pretty much a complete linux newbie, so could you be as precise as possible in your suggestions?)[/QUOTE]

Edit /etc/X11/XF86Config-4 and replace the "ati" or "radeon" driver with "fglrx". 
:)

---

### Post by FLeiXiuS on 2004-10-26
[QUOTE=NeiL]Edit /etc/X11/XF86Config-4 and replace the "ati" or "radeon" driver with "fglrx". 
:)[/QUOTE] 
Also, install the ATI drivers for your current card, you can check the Ubuntu FAQ / WIKI for more details.

---

### Post by wallijonn on 2004-10-31
at the # prompt run fglrxconfig

# fglrxconfig

---

