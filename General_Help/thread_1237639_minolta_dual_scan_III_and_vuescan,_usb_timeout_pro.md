---
title: "minolta dual scan III and vuescan, usb timeout problem."
date: 2009-08-11
forum: General Help
---

### Post by dkrooshof on 2009-08-11
Dear all,

I have a Minolta dual scan III negative scanner that I use with vuescan. When the scanner is performing a long scan it sometimes suddenly halts. Vue scan doesn't respond anymore when this happens and needs to be killed.
On the vuescan release notes there is a remark about this problem, but I do not know what it means ans how I can fix it. It says this:

([http://www.hamrick.com/vuescan/vuescan.htm#linux](http://www.hamrick.com/vuescan/vuescan.htm#linux))

[I]
"...If you're having problems with USB timeouts (i.e. with the Nikon CoolScan IV (LS-40), make sure you use the "usb-uhci" (CONFIG_USB_UHCI) module instead of the alternate "uhci" (CONFIG_UHCI_ALT) module. You might also increase the kernel usb timeout value (CONFIG_USB_LONG_TIMEOUT=y)..."[/I]

I do not know how to check if I have a certain module in my kernel or not, and how to make any changes. Could someone please give me a hint?

uname -a:
Linux dkrooshof-laptop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

---

### Post by dkrooshof on 2009-08-13
Anyone please?

---

