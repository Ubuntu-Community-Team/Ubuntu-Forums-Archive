---
title: "Getting Brother DCP-1000 printing and scanning"
date: 2011-07-22
forum: General Help
---

### Post by 999alfred on 2011-07-22
I was given a Brother DCP-1000 printer/scanner/copier Copy works fine) and I am trying to get it to work under Lucid Lynx.

I hook it up USB and with cups search for new printers and it is found and I install it with driver DSP-1200-CUPS+Gutenprintv5.2.5(grayscale).

I then try to print a test page and the printer display says "Receiving Data" and the job shows (It seems to take longer than the test page to my okidata laser). Then the job finishes and the printer displays "Sleep Mode" and never prints.

Why no print?

Also I started xsane and it searched for scanners and found none. SO, how do I get the scanning to work also?

tj

---

### Post by plucky on 2011-07-23
> **999alfred said:**
> I was given a Brother DCP-1000 printer/scanner/copier Copy works fine) and I am trying to get it to work under Lucid Lynx.

I hook it up USB and with cups search for new printers and it is found and I install it with driver DSP-1200-CUPS+Gutenprintv5.2.5(grayscale).

I then try to print a test page and the printer display says "Receiving Data" and the job shows (It seems to take longer than the test page to my okidata laser). Then the job finishes and the printer displays "Sleep Mode" and never prints.

Why no print?

Also I started xsane and it searched for scanners and found none. SO, how do I get the scanning to work also?

tj


You probably need to install the drivers.

Open Synaptic Package Manager and search for **dcp-1000** and you should find ```
brother-cups-wrapper-laser1
brother-lpr-drivers-laser1
```
Select both and install.

After install,connect and power up the printer.

Go to System > Administration > Printing and Add a new printer and select the correct drivers for your printer which should now be in the list of Brother drivers.

For the Scanner go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and download the correct .deb driver for your scanner and install.Instructions are provided on the website.

Good Luck

---

