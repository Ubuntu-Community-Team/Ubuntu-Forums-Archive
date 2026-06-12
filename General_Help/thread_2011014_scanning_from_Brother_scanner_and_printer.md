---
title: "scanning from Brother scanner and printer"
date: 2012-06-26
forum: General Help
---

### Post by rasmus91 on 2012-06-26
Hey

I can't seem to use xsane to scan from my parents Brother LC-1000 BK printer with buitin scanner. but i can't really use it, if i press scan to file, then it says "connecting to PC" but nothing seems to happen.

can someone offer some insight?

---

### Post by sudodus on 2012-06-26
Check at the manufacturer's home page, if there is a linux driver for your scanner-printer!

I have a Brother printer, and downloaded and installed a driver from there. It works for me, and I think it will work for you too :-)

---

### Post by Jose Catre-Vandis on 2012-06-26
**Brother LC-1000 BK  << this is a black cartridge.**

What is your Printer Model?

Normally printer drivers are in the repos and you have to go to the Brother website and follow instructions to install your scanner driver

---

### Post by TheFu on 2012-06-26
I have a Brother All-in-One MFC-240C (fax, scanner, printer) and use **gscan2pdf** to scan without issues.  Pressing the **Start **button (black/color) on the scanner doesn't start the scanning - that is controlled in the software, at least for my device.

I don't recall having to download any drivers from the "Brother" website.  Oh, and don't go to the "brothersoft" website, it is filled with malware and worse.

---

### Post by rasmus91 on 2012-06-26
its actually a DCP-350C (that helps quite a bit) 

> Brother LC-1000 BK << this is a black cartridge.

I thought that was something different, but thats what my father said. Those parents, Not a very good understanding of IT they have.

---

### Post by davidvandoren on 2012-06-26
Go [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)
here and download the driver for printer and scanner

then do this to make the scanner work
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04

```

**1.** sudo gedit /lib/udev/rules.d/40-libsane.rules

```
**2. **Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
  
  
  The lines to be added---------------------------               ```
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
``` 
Then press save and close the text editor window 
**3.** Restart the OS.

---

