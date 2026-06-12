---
title: "Installing Wireless Printer on Ubuntu"
date: 2010-05-21
forum: General Help
---

### Post by davmes on 2010-05-21
Hi,

I have a Canon PIXMA MP628 printer connected to my home network, wirelessly. PReviously, when I was running windows, I am able to print wirelessly.

My printer is connected to my router and has a static IP address of 192.168.0.199

Therefore, how can I make my printer to work in Ubuntu now, since Canon doesn't have any Linux drivers. Am I able to add printer from Ubuntu Printing Service menu? What are the options that I should select?

---

### Post by cariboo on 2010-05-21
There are drivers for some Canon mp printers available [here]("http://www.canon-europe.com/Support/Software/Linux/PIXMA/index.asp")

---

### Post by davmes on 2010-05-21
Hi,

Apprently I went to the website and was unable to see any download links. Therefore, I did my own search, with your reference, and found this file:

cnijfilter-common_3.00-1_i386.deb

I tried installing this package but had difficulties. In the end, I had to type "sudo apt-get install -f" to remove the package.

I am using Ubuntu 10.04.

Need some help here. I can't print.

---

### Post by kev77 on 2010-05-21
found a blog that may shed some light! [http://mp610.blogspot.com/]("http://mp610.blogspot.com/") sometimes linux drivers will support USB only, no wifi, (as is the case with our lexmark x4650!) so i would setup your machine via USB until you are sure of wifi support. also [this]("http://www.openprinting.org/drivers") website may be useful.  :)

keep us posted on your progress!

---

### Post by davmes on 2010-05-22
I think I am stuck here while trying to install recommended canon drivers:

dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common

I tried install libcupsys2 but was informed that libcups2 is the newer version...

So, in a way, the 'latest' 3.0 canon drivers is incompatible with Ubuntu 10.04?

---

### Post by davmes on 2010-05-23
Hi there,

Is there anyone who can help me out? Apparently the customer support from Canon asked me to download their MP638 drivers and I have them, and it just couldn't work..

---

