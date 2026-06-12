---
title: "HP Deskjet 1000 on Ubuntu 10.04"
date: 2011-07-23
forum: General Help
---

### Post by subhadip_sky on 2011-07-23
Hi, I got this strange problem while installing an HP Deskjet 1000 printer on my friends Ubuntu 10.04 desktop. We followed all the steps mentioned in different tutorials, first tried the simple way, went to system>administration>printing and installed new printer, everything was ok until we went for the test print option, it just won't print. One thing I noticed there was that it won't show the marker/ink level, I don't know if it's for not detecting the printer correctly although the cartridges were properly installed.
Then I tried the other way, installed the hp-toolbox but got no luck there too!
 I never used a printer on my own computer before and I really have to find a way to do this right because I got him turned onto Ubuntu and now I don't want him to go back. And besides I heard HP has an excellent support on Ubuntu computers. Please help!

---

### Post by Tamlynmac on 2011-07-24
One quick way to identify if an HP printer is compatible with Linux is to confirm it [here]("http://hplipopensource.com/hplip-web/supported_devices/index.html"). I often refer to that site when asked if a printer is Ubuntu/Linux compatible.
  
  Based on the HP model number you posted, it appears that the printer  isn't supported by the HPLIP driver. Neither the Deskjet 1000 "cxi" or  "cse" are supported. I read that some success has been had by using the HPLIP 3.10.9 driver,  especially if your printer is a J110 series. But I cannot personally  confirm said success.
 
 IMHO, Ubuntu may not be for everyone and should  this be a deal breaker than one needs to question the commitment. Keeping in mind, that all OS's require compatible hardware. I might suggest future support request not use the element of failure,  as a motive for returning to a different OS. It's been used many times  and I've read that some members simply ignore those types of requests.

 Good Luck

---

### Post by subhadip_sky on 2011-07-24
Thank you.

---

### Post by subhadip_sky on 2011-07-25
Thank you for the information! Installing hplip version 3.11.5 did the trick. Actually the default version in Lucid is 3.10.2 which does not support the HP Deskjet 1000 J110 series.:D

---

### Post by subhadip_sky on 2011-07-28
Check out [this]("http://subhadipghosh.wordpress.com/2011/07/27/hp-deskjet-1000-printer-j110-series-on-ubuntu-10-04-lucid/")

---

