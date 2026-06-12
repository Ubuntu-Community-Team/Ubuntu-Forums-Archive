---
title: "Huawei e220 usb modem"
date: 2009-10-15
forum: General Help
---

### Post by Quest1on on 2009-10-15
Hello , i have a problem. I got a usb modem Huawei e220 with Orange nad it is not working. When i pluged it in the first time , it asked me the country , operator etc. Now when i connect it it says connection established but no internet . A hand pls. tx

---

### Post by phillw on 2009-10-15
> **Quest1on said:**
> Hello , i have a problem. I got a usb modem Huawei e220 with Orange nad it is not working. When i pluged it in the first time , it asked me the country , operator etc. Now when i connect it it says connection established but no internet . A hand pls. tx

This is a gremlin !!! - and it drives me mad... Simply click on the connect icon again. (Sometimes takes a couple of goes).

That isn't an answer - but it is a way round it. 3, my supplier tells me that they do not 'per-se' support the hawaii modems on linux. But, apart from that annoying little gremlin - I get on fine with mine :)

Hope that is of help.

Phill.

---

### Post by Quest1on on 2009-10-15
It is not working :( Any other ideas? Thank you .

---

### Post by rlogan on 2009-10-19
I had a friends machine have problems with this device. What I found was that one setting needed adjusting, I type up a quick thing about it.

Check it out here 

[http://thejungleonline.wordpress.com/2009/10/10/get-huawei-e220-3g-modem-working-under-ubuntu-jaunty/](http://thejungleonline.wordpress.com/2009/10/10/get-huawei-e220-3g-modem-working-under-ubuntu-jaunty/)

Hope it helps

Richard

---

### Post by shuttleworthwannabe on 2009-10-19
As far as I know Jaunty should be able to pick the USB and prompt user to connect (when done the first time); thereafter, under network manager, the connection will be visible to select. Ibex network manager was not plug 'n play--needed some kind of setup. OR try this [link]("https://forge.vodafonebetavine.net/projects/vodafonemobilec/")

---

### Post by t0p on 2009-10-19
Are you *absolutely sure* that network manager is using the correct login credentials to connect to Orange?  When I first used my Huawei E160X, I went through the process of telling network manager's wizard the details of provider, country etc, but could not connect properly because network manager was trying to connect the wrong Access Point - I use Vodafone Top Up and Go, but network manager tried the prepay Access Point.  I had to edit the settings manually to change it to the correct Access Point.

If you search the web, you will find the correct details for your provider and mode of connection (ie prepay or contract).  Or ask Orange.  Just remember, if ou call Orange customer services, they will probably tell you that the modem doesn't work with Linux.  Just ask them for the Access Point login info - username, password and Access Point name.

---

### Post by shuttleworthwannabe on 2009-10-19
Hi guyz, [this may help]("http://www.ubuntugeek.com/launch2net-mobile-internet-connection-manager-for-ubuntu.html").

---

### Post by rlogan on 2009-10-19
From what I have found with this device it is 99% setup automatically for the E220 and only needs the method to be set correctly with the ISP I have had the devices for.

---

### Post by ^_Pepe_^ on 2009-10-22
Hi guys!

I think there's a kernel problem affecting also E220 modems.

Please take a look to this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146).

I have a e220 working perfectly in 9.04, and I have no plans to upgrade until fix released.

Regards
^_Pepe_^

---

