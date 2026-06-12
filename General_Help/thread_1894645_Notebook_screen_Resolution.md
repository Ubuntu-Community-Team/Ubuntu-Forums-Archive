---
title: "Notebook screen Resolution"
date: 2011-12-13
forum: General Help
---

### Post by arnotsmith on 2011-12-13
I have just installed Ubuntu 10.04 on a Lenovo Thinkpad E420.
The specified screen resolution is 1366x768, but all I can get is 1024x768, and the screen is "Unknown".The following dump may help:

gillian@LR9K83CC:~$ lspci | grep 'VGA'
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6741
gillian@LR9K83CC:~$ xrandr
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
gillian@LR9K83CC:~$

---

### Post by arnotsmith on 2011-12-13
I guess that there is a proprietary driver problem here.

The Intel controller should be recognisable, so how do I persuade Ubuntu to use:
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)

and to ignore:
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6741

- can anyone help?
Please?

---

### Post by Mark Phelps on 2011-12-14
Looks like you have one of the "dreaded" switchable graphics PCs.  These were designed to automatically switch between video chipsets based on demand -- and raise havoc with Linux distros.

Maybe the info in the link below will help:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by arnotsmith on 2011-12-14
Thanks Mark, it looks like I really stuffed up that configuration. My bad.

Regards,
Peter

---

