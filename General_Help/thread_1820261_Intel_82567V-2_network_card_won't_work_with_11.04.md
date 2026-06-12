---
title: "Intel 82567V-2 network card won't work with 11.04"
date: 2011-08-07
forum: General Help
---

### Post by stevemahfouz on 2011-08-07
My problem is similar to this one ( [http://ubuntuforums.org/showthread.php?t=1276211]("http://ubuntuforums.org/showthread.php?t=1276211")  ) and I've already tried some of the steps, to no final resolution.

The OS in question: Ubuntu 11.04 64 bit
Problem hardware: Intel Ethernet 82567V-2 network card
URL for Linux drivers for hardware: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng&OSVersion=Linux*&DownloadType=Drivers]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng&OSVersion=Linux*&DownloadType=Drivers")

I've already installed the latest driver using the README instructions (sudo make install, etc).

The network card will connect ONLY to my Linksys router but not even to my Motorola cable modem, even when it's directly connected to the modem ! I cannot get any web pages at all outside of my LAN, only my Linksys configuration page on my router.

As I said above, I've already tried most of the steps in that forum post above. I'm going back to retrace my steps to see what else I can do. 

Thanks for your time and your help. BTW, my motherboard is the Asus Rampage III Formula.

Steve

---

### Post by stevemahfouz on 2011-08-12
> **stevemahfouz said:**
> My problem is similar to this one ( [http://ubuntuforums.org/showthread.php?t=1276211]("http://ubuntuforums.org/showthread.php?t=1276211")  ) and I've already tried some of the steps, to no final resolution.

The OS in question: Ubuntu 11.04 64 bit
Problem hardware: Intel Ethernet 82567V-2 network card
URL for Linux drivers for hardware: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng&OSVersion=Linux*&DownloadType=Drivers]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3003&lang=eng&OSVersion=Linux*&DownloadType=Drivers")

I've already installed the latest driver using the README instructions (sudo make install, etc).

The network card will connect ONLY to my Linksys router but not even to my Motorola cable modem, even when it's directly connected to the modem ! I cannot get any web pages at all outside of my LAN, only my Linksys configuration page on my router.

As I said above, I've already tried most of the steps in that forum post above. I'm going back to retrace my steps to see what else I can do. 

Thanks for your time and your help. BTW, my motherboard is the Asus Rampage III Formula.

Steve

Never mind, Bug #824591 filed.

---

