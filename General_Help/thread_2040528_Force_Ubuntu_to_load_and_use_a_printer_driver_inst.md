---
title: "Force Ubuntu to load and use a printer driver instead of the default one."
date: 2012-08-11
forum: General Help
---

### Post by Bjorg on 2012-08-11
Hi,

I have a Dell 1815dn printer.

Ubuntu recognizes it automatically and installs a default driver. But this driver lacks the option to bypass the toner-saver function which is very important for me since some times I want no toner-saver function as I need more contrast.

I have a propietary .ppd file from Dell that I have been using in past Ubuntu releases, and even in another computer with 12.04. But now I don't now how to force Ubuntu to skip the default driver and load the one I have (for some reason I got Ubuntu to ask me for the .ppd file, now I don't now how). 

Any help on how to do this?

My prefered solution would be that the GUI asks me for the .ppd I have and load it, as I always have done. Another solution would be to know the folder in which I need to put the propietary .ppd file and force Ubuntu to use it.  

Thanks,

Alex

---

### Post by Bjorg on 2012-08-12
Solved:

To bring the dialog box that was present in past releases, in a terminal put:

$ system-config-printer

---

