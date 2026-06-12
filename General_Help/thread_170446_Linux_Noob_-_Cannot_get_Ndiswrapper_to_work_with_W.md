---
title: "Linux Noob - Cannot get Ndiswrapper to work with WEP"
date: 2006-05-04
forum: General Help
---

### Post by zead on 2006-05-04
I can't seem to get Ndiswrapper to work with WEP, if I setup my access point with no security it works fine but I just can't seem to get it to work with security.
I am a Linux noob and therefore using the Ndisgtk gui for Ndiswrapper. I have tried with Ascii and Hexadecimal but it just doesn't work:( 

My best guess is that the security side of the Ndisgtk Gui doesn't seem to be setting the WEP key correctly. 
How do I go about setting the WEP key using the command prompt?

HP nx9105 Laptop
Broadcom BCM4306 wireless using bcmwl5a driver
Ubuntu 5.10 with the latest updates
Oh and I used Synaptic manager to install Ndiswrapper and Ndisgtk.

---

### Post by joelito on 2006-05-04
You can get gtkwifi from the forums, it should help you better locate and setup your encrypted network.

---

### Post by Michael Steinberg on 2006-05-04
I've had good luck with NetworkManager. It can be flaky sometimes, but my laptop is as reliable in finding our home network--WEP protected--as my wife's Apple PowerBook, and it's less sensitive to changes in location within the house, too.

BTW, I used the GUI for ndiswrapper, too, and before using NetwordManager I recall using the Network configurator under the System menu to put in the WEP key for my default configuration. (I've used NetworkManager to access other networks.)

---

