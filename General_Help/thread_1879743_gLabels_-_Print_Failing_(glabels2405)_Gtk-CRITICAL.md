---
title: "gLabels - Print Failing (glabels:2405): Gtk-CRITICAL"
date: 2011-11-12
forum: General Help
---

### Post by Andrew1234 on 2011-11-12
[PHP](glabels:2405): Gtk-CRITICAL **: IA__gtk_print_operation_set_n_pages: assertion `n_pages > 0' failed
[/PHP]

I had a problem with my 11.04 install and had to re-install from livecd.
Since then I am getting the above error when trying to print gLabels.


glabels 2.2.8

---

### Post by Andrew1234 on 2011-11-14
Done a little digging and I feel I have had this problem since I tried to install adobereader-enu which failed - install, I have tried to unistall via apt-get remove and also re-install adobereader and then once installed removed. But I still get this error...

I have now updated to 11.10 but still have the same issue, I have reinstalled gtk2, glabels. Glabels was working fine I feel it really is something to do with the adobe install.

[PHP]andrew@andrew-desktop:~$ sudo apt-get remove adobereader-enu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'acroread' instead of 'adobereader-enu'
Package acroread is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
andrew@andrew-desktop:~$ sudo apt-get remove adobereader
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package adobereader
[/PHP]

The above does show 3 'not upgraded' if I have uninstalled this program why does it show these three not upgraded.

---

