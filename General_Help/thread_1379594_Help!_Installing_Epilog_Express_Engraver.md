---
title: "Help! Installing Epilog Express Engraver"
date: 2010-01-12
forum: General Help
---

### Post by OttoFalcon on 2010-01-12
My dad owns a business and the computer he uses for engraving uses Windows 98 and he wants to upgrade and he likes ubuntu and I want to know how to install an Epilog Laser Engraver model 2000 25a laser!

Thank u!

---

### Post by mrichards0 on 2010-01-19
I inherited and repaired an Epilog Express 100 and have been having a great time with it.  The old Windows XP machine died that was running it and I had to replace it.  

When I ordered the new machine from Dell, I got a Windows 7 64 bit OS.  The new Windows Vista and 7 drivers from Epilog were only 32 bit drivers and it didn't work.  *This is something to think about if your dad upgrades his computer.*  I was able to get it working using a [COLOR="Blue"]_[TrendNet parallel print server]("http://www.trendnet.com/products/proddetail.asp?prod=120_TE100-P1P&cat=46")[/COLOR]_ and [COLOR="Blue"]_[VMware Player]("http://www.vmware.com/products/player/")_[/COLOR] running Vista 32 bit.  Using Unity mode, you almost can't tell Corel Draw is running in a virtual machine.  This worked great for me.  

In the process a friend donated an old Shuttle computer running XP.  I was happier with the print server, so I installed [COLOR="Blue"]_[Ubuntu Studio]("http://ubuntustudio.org/")_[/COLOR] on the Shuttle.  I found an Epilog driver for Linux called [COLOR="blue"]_[cups-epilog.c]("http://aa.gg/free/")_[/COLOR].  Reason to do this, a quote from this website, *"The Epilog laser engraver comes with a windows printer driver. This works well with Corel Draw, and that is about it. There are other windows applications, like inkscape, but these rasterise the image before sending to the windows printer driver, so there is no way to use them to vector cut!"*  This appears to be a driver for the Epilog Legend, however he posted the source code.  I compiled the driver and installed it, following his instructions on the website.  I haven't been successful from Linux yet (this was all done last night), but I'm going to spend some more time trying.  I'm getting an error (cups-insecure-filter), which seems more like a driver error than an incompatibility error at this point.  Maybe you can try or others can help.

---

### Post by mrichards0 on 2010-01-19
I figured out the error, it was because I copied the driver to the cups directory and didn't change the ownership to root.  It starts the laser cutter, but what it engraves doesn't look like what I'm printing.  It prints garbage almost in the form of the text I'm printing.  It also starts from the bottom and engraves up.  I emailed Epilog and asked for the command codes, so I can fix the driver.  Hopefully they'll send them and I can send you the fixed driver.

---

