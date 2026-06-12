---
title: "HOWTO: Ubuntu Netbook Remix 9.04 on HP Mini 5101"
date: 2009-09-16
forum: General Help
---

### Post by misha680 on 2009-09-16
Here are some notes. Adapted from [http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/) very helpful.

1. Download here:
[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

Follow instructions to install on flash (1GB or larger):
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

2. Boot up your system. On boot press F10 to go into configuration

Go to System Configuration -> Device Configuration -> Dual Core CPU and disable

[http://ubuntuforums.org/showthread.php?t=1115691](http://ubuntuforums.org/showthread.php?t=1115691)

the N280 Atom only has one core anyway
[http://ark.intel.com/Product.aspx?id=41411](http://ark.intel.com/Product.aspx?id=41411)

Personally, I prefer the Function Key Switch to be Enabled as well, but that is personal preference.

3. Go to File -> Save Changes and Exit and press F10.

4. Now when the computer boots up (make sure your flash is inserted) press F9 and select USB Flash Drive. Boot off of it and
install Ubuntu Netbook Remix (I will leave a gap here - plenty of info about this).

5. Once installed:

You want an updated version of the wl driver that supports the broadcom 4353 module (there is an NDISwrapper alternative here but that did not seem to work for me:
[http://ubuntuforums.org/showthread.php?t=1263730](http://ubuntuforums.org/showthread.php?t=1263730)
)

I adapted this from (rather copy & pasted)
[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

"This is easy — you just need to install the driver back-ported from the next Ubuntu release.

First, enable the backports repository: Administration > Software Sources > Updates and enable “Unsupported Updates (jaunty-backports)”.

Then, open Synaptic Package Manager, find the package linux-backports-modules-jaunty, and install it."

Also, you will need to install linux-restricted-modules if you haven't. I am not sure if this is automatic or not.

Finally, you might need to go to System -> Administration -> Hardware Drivers and enable the Broadcom Wireless chipset. Enjoy!

p.s. More info:

2gb RAM modules
[http://www.hpminiguide.com/forums/viewtopic.php?p=16430](http://www.hpminiguide.com/forums/viewtopic.php?p=16430)

This ebay seller seems to have compatible keyboard covers:
[http://myworld.ebay.com/komazys?ssPageName=ADME:X:CEM:US:1181](http://myworld.ebay.com/komazys?ssPageName=ADME:X:CEM:US:1181)

radtech will cut ScreenSaverz for this netbook
Nushield will make screen protectors

still looking for a cover for the whole thing a la
[http://stores.shop.ebay.com/3acp__W0QQ_armrsZ1QQ_fsubZ487078016](http://stores.shop.ebay.com/3acp__W0QQ_armrsZ1QQ_fsubZ487078016)

will ask if this works

---

