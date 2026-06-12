---
title: "Xerox Printer Printing Wrong Colours"
date: 2012-08-23
forum: General Help
---

### Post by Maheriano on 2012-08-23
I just bought a new printer, it's a Xerox Workcentre 6015 but it's not printing the proper colours.

The test page seems to come out properly, does this look right?

[IMG]http://www.danmaher.com/images/printer1.jpg[/IMG]

This is the way the image is supposed to look:

[IMG]http://www.danmaher.com/images/printer3.jpg[/IMG]

And this is how it comes out of my printer. Any ideas?

[IMG]http://www.danmaher.com/images/printer2.jpg[/IMG]

The images look the same when printed from multiple different Ubuntu machines and multiple different images.

---

### Post by gellert.gyuris on 2012-08-29
Same bug described here: [http://ubuntu.hu/node/30585](http://ubuntu.hu/node/30585) But no solution. :(
Here is the LP bug report: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424)

---

### Post by Maheriano on 2012-09-04
Thanks, I took another look at the driver I was downloading from the Xerox website and it says it's for 32 bit machines only. The printer specifically says it's compatible with Linux, why wouldn't they create a 64 bit driver? Isn't this 2012?

---

### Post by gellert.gyuris on 2012-09-10
Hi Maheriano,
Here is a solution for 64bit: [http://linuxliberations.blogspot.hu/2012/08/printing-with-xerox-workcentre-6015ni.html](http://linuxliberations.blogspot.hu/2012/08/printing-with-xerox-workcentre-6015ni.html) I tested it, but no result: the colour bug remains :(

---

### Post by gellert.gyuris on 2012-09-14
Hi Maheriano,
Please, come to Launchpad for bug hunting. We should be make some tests.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/984424)

---

### Post by Maheriano on 2012-10-15
> **gellert.gyuris said:**
> Hi Maheriano,
Here is a solution for 64bit: [http://linuxliberations.blogspot.hu/2012/08/printing-with-xerox-workcentre-6015ni.html](http://linuxliberations.blogspot.hu/2012/08/printing-with-xerox-workcentre-6015ni.html) I tested it, but no result: the colour bug remains :(

I also tried this, didn't work.

---

### Post by GerryGG on 2012-12-03
This is not just a 64 bit problem. I installed the 6015NI on my Ubuntu 12.04 32bit system, using the Xerox deb package, and have the same color problem. Fortunately, I just got this printer, and so I will be returning it.

---

