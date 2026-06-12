---
title: "How do I configure sane backend? Canon Pixma MX330"
date: 2009-10-25
forum: General Help
---

### Post by thirdrev on 2009-10-25
I have a canon mx330. Printer works, scanner does not.
sane-find-scanner yields:
found USB scanner (vendor=0x04a9, product=0x1737) at libusb:001:003

xsane says "no devices available"
scanimage -L yields "No scanners were identified."

according to the sane page I need the pixma backend, but it doesn't tell me how to implement it. 
The libsane-pixma files necessary seem to be in place in /usr/lib/sane; there was not a conf file in /etc/sane.d so I created pixma.conf and wrote: "usb 0x04a9 0x1737" in the file... to no avail.

If anyone has information on how to use the pixma backend or has experience getting another canon pixma working with xsane, your input would be greatly appreciated.

---

### Post by thirdrev on 2009-10-26
Looks like I found the answer to my question. Anyone trying to get the pixma backend to work and having problems may want to take a look at:
[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

---

### Post by jimmuhs on 2011-07-14
My MX330 can scan now!
Many thanks.

---

