---
title: "xsane scanner error - permissions related"
date: 2010-02-11
forum: General Help
---

### Post by HereInOz on 2010-02-11
Hi All,

I have installed a Brother MFC-250C printer/scanner.  The printer works fine, but when I open XSane to scan, I receive an error as follows:

Failed to open device 'brother3:bus2;dev1': Invalid argument

And XSane then closes.

The interesting thing is that if I open Xsane from a terminal using sudo xsane, it will open correctly and allow me to scan, with the warning about being a root user.  (It also creates a file with only root permissions, so this is not entirely ideal).

This looks like it is a permissions issue of some description, so if someone can tell me where to start looking and which permissions I need to modify, I would be really appreciative.

Hope you can help.

---

### Post by plucky on 2010-02-11
> **HereInOz said:**
> Hi All,

I have installed a Brother MFC-250C printer/scanner.  The printer works fine, but when I open XSane to scan, I receive an error as follows:

Failed to open device 'brother3:bus2;dev1': Invalid argument

And XSane then closes.

The interesting thing is that if I open Xsane from a terminal using sudo xsane, it will open correctly and allow me to scan, with the warning about being a root user.  (It also creates a file with only root permissions, so this is not entirely ideal).

This looks like it is a permissions issue of some description, so if someone can tell me where to start looking and which permissions I need to modify, I would be really appreciative.

Hope you can help.



Checkout the [Brother Solutions Center](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) for further information.

Especially [here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)


Good Luck

---

