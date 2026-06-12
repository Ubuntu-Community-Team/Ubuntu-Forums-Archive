---
title: "wireless on 1215T 64-bit - linux netbook"
date: 2011-03-06
forum: General Help
---

### Post by freedomAboveAll on 2011-03-06
Hello - just bought the following awesome little laptop/netbook for $350 that comes with no Microsoft pre-installed:

ASUS Eee PC 1215T-MU10-BK Black AMD Athlon II Neo K125(1.70GHz) 12.1" WXGA 2GB DDR3 Memory 320GB HDD NetBook
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834220857](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220857)

Installed 10.10 64bit desktop via USB stick and activated the Broadcom drivers.

The wireless card not detected. Could this be due to the 64bit version?  I purchased same computer for family & installed the 32 bit without a hitch.  

Ifconfig shows eth0, eth1, and lo.

The issue could easily be a hardware issue imo, since Asus  is cranking out so many different netbooks lately - i had to rma an earlier  model of Asus, which they did in most excellent manner.

Thank you for any help as to my questions.

---

### Post by freedomAboveAll on 2011-03-06
** oops ** 

F2 to go to BIOS , enabled WLAN and wireless now works.
btw - this computer also has Bluetooth support which  has to be enabled in BIOS.

hmm. how to mark thread solved ...

---

### Post by freedomAboveAll on 2011-03-06
in hopes of not violating anyones ethics -

[http://www.accessdataservices.com/blog/](http://www.accessdataservices.com/blog/)

and

[http://citystatedata.com/](http://citystatedata.com/)

are my sources of data.

G

---

### Post by adrian.limpin on 2011-04-13
for the other readers, in case it still doesn't work, I found that you still have to update the proprietary wlan driver (which you could update along with the graphics driver).

---

### Post by freedomAboveAll on 2011-04-14
> **adrian.limpin said:**
> for the other readers, in case it still doesn't work, I found that you still have to update the proprietary wlan driver (which you could update along with the graphics driver).

Yes.  1 step is to plug in to a wired Ethernet.  Do the update & install restricted drivers over an ethernet cable.  That will install the Broadcomm wireless drivers.

---

