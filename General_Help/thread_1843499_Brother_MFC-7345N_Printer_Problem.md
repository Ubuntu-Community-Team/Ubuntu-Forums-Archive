---
title: "Brother MFC-7345N Printer Problem"
date: 2011-09-13
forum: General Help
---

### Post by gabo.cr on 2011-09-13
Hi

I was able to install a Brother MFC-7345N printer over the network. The problem that I have is that every time I print is just printing blank pages nonstop. So I have to cancel the print job on the printer.

So my guess is that the printer is correctly installed since is sending jobs, but I don't know why they are blank. I restarted my computer and printer and the problem is persisting.

I'm using a Dell Inspiron 1525 with Lucid 10.04.

This is the Cups info:

Description:	Brother Brother MFC-7345N
Location:	Brother Brother MFC-7345N
Driver:	Local Raw Printer (grayscale)
Connection:	dnssd://Brother%20MFC-7345N._pdl-datastream._tcp.local/
Defaults:	job-sheets=none, none media=unknown 

I appreciate any suggestions.

---

### Post by gabo.cr on 2011-09-13
bump

---

### Post by walt.smith1960 on 2011-09-13
Where did you get the driver?  If you didn't get it from Brother's web site, you might try uninstalling then reinstalling the downloaded .deb file(s) from here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7345N](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7345N)
The directions cover all distros and are more complex than they need to be for Ubuntu.  If you're using 32 bit Ubuntu you can install the .deb file using Ubuntu software center or via the command line.  Either one will work.  If you're using a 64 bit O.S. you must use the command line because you need the " dpkg  -i  **--force-all**  (lpr-drivername). Most of the "pre-install" instructions are not relevant to newer Ubuntu distros.  Do pay attention to the instructions on the scanner install.  You must have CSH or TCSH from the repositories, be sure sane-utils is installed and some other stuff.

---

### Post by gabo.cr on 2011-09-13
That same page is the one that I used.
But I didn't see Step 5b. (for Network Connection).
So I followed those instructions and I don't know how to get the IP address from my printer.
I was able to print the "Network Configuration" directly from the printer and the IP that it printed was: 0.0.0.0.
The thing is that the printer is connected to the router, so it should be getting an IP address from it.

I decided to go crazy and I added:
Connection: lpd://0.0.0.0/binary_p1

But is not working, now the printer is getting no data from my computer. It was getting data before but printing blank pages. So I don't know what to do.

---

### Post by gabo.cr on 2011-09-13
It is working now !

I previously had:
Driver: Local Raw Printer (grayscale)

But I changed it to:
Driver:	Brother MFC7340 for CUPS (grayscale)

The connection is the same as before:
dnssd://Brother%20MFC-7345N._pdl-datastream._tcp.local/

I forgot to mention that we have a apple router, call me crazy but this router is not very impressive.

---

### Post by walt.smith1960 on 2011-09-14
I'm glad you were able to get it to work. If you find that your network connection becomes unreliable here is what has been consistently reliable for me.  In the device URI windows put:  [http://socket](http://socket) xxx.xxx.xxx.xxx where x are the i.p. address. The caveat is that the printer must have a static i.p. address.  I have 2 Brother MFC devices, both have displays and were easy to set up.

---

