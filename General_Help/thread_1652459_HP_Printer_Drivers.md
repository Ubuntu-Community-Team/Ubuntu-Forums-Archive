---
title: "HP Printer Drivers"
date: 2010-12-24
forum: General Help
---

### Post by octocat on 2010-12-24
Hey guys, I recently got a HP Wireless D110a printer. I'm using Pinguy OS, which uses Ubuntu 10.10. I went to the HP site and got the linux drivers because the disk does not support linux. I downloaded the drivers and when im running it in terminal it get an error mid way saying i need the python development files. So i go about and download and install them. Run the drivers again, same thing, need python development. What am I doing wrong? What do I do?

---

### Post by dE_logics on 2010-12-24
Question is what are you doing right.

Open up synaptic and see if hplip package is installed, if so, stuff are just plug and play.

And quit the habit of download stuff and installing like you used to do in Windows, use the repository instead.

---

### Post by JC Cheloven on 2010-12-24
Hi, just checked [here]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=2020&lc=en&cc=us&dlc=en&sw_lang=&product=4023246"), an although it leads to a site currently under maintenance, it seems that it'll point you to the common hp linux printing and imaging driver, hplip. I believe it's loaded by default in ubuntu (don't know in pinguy though). If so, you shouldn't need anything else.

EDIT:sorry, dE_logic answered almost identically while I searched/wrote.

---

### Post by octocat on 2010-12-24
hplip is installed. what do i do now?
thanks for the help so far.

---

### Post by reid_rsv869 on 2011-01-06
Just a side question guys...

How complete is the collection of HP drivers for the OS community?  That is, I'm willing to go buy a new HP printer but worry the drivers might not be available.  

Just BTW... I run ubuntu 10.10 and update in the standard fashion.

Thanks

Reid

---

### Post by coffeecat on 2011-01-06
Go to System > Adminstration > Printing. Click on the 'Add' button. Highlight 'Other' and under Device URI, type 'http://' (without the quotes). Click on Forward. Tick 'Select printer from database', and highlight 'HP'. Click on Forward and you get a list of all the HP models supported out of the box. Ditto for other makes.

In the unlikely event that the  printer you want is not listed, have a look here:

[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

Look up the particular model and there may be more information, including driver download links.

---

### Post by CoolJohnB on 2011-01-06
With my HP & Cannon printers I just plugged them in, and that was it!  Ubuntu did the rest as the comment above says Ubuntu is truly Plug and play, also it's very intuitive, can't understand why anyone would want to use windows!

---

