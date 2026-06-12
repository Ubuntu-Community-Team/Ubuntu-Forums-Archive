---
title: "Feedback on Ubuntu 11.10 - Sony VGN-NW250F Laptop Performance"
date: 2011-11-06
forum: General Help
---

### Post by Nipper007 on 2011-11-06
I installed Ubuntu 11.10 64-bit version on my [Sony VGN-NW250F]("http://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&partNumber=VGNNW250F/S#specifications") laptop after I previously had Ubuntu 11.04 64-bit installed.  I notice a great performance difference between these two versions.  Aside from the horrible Gnome desktop in 11.10 compared to 11.04, I cannot determine why Ubuntu 11.10 performance is horrible.  I also had installed Fedora 15 64-bit for a test where Fedora 15 ran fast on this same system.  With all the negative media coverage that I have read on Ubuntu 11.10, I doubt that I will continue to use Ubuntu at this time.  I may try Ubuntu again with version 12.04 (not sure when of when it will get released).

I had installed Ubuntu 11.10 32-bit on this same laptop a while back and it also ran slow.  The Ubuntu performance was so bad where I could not stand it and went back to using Windows 7 64-bit version on the laptop (dual boot).

In Fedora 15 (32/64-bit versions), the web cam on the Sony laptop will not work in Skype 2.2 beta.  The Sony web cam works in Skype 2.2 beta in Ubuntu 11.10 64-bit version.  However in Skype, the audio does not work.  This problem seems more like a Skype issue.  In both Fedora and Ubuntu versions, Cheese worked with the web cam, unsure of the audio.  I did not test the audio in Skype 2.2 beta until I knew the video would work.  Audio works in all other apps.  Note - the video would not work in Ubuntu 11.04 (32-bit and 64-bit versions).

I am just providing my feedback on my experience with Ubuntu 11.10 where I had hoped to continue my use of this linux distro.  Hopefully someone knows of something that would help the Ubuntu 11.10 performance on this laptop.  Ubuntu 11.04 ran fast, Ubuntu 11.10 runs horribly slow.

Thanks.

---

### Post by Nipper007 on 2011-11-06
> **Nipper007 said:**
> I installed Ubuntu 11.10 64-bit version on my [Sony VGN-NW250F]("http://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&partNumber=VGNNW250F/S#specifications") laptop after I previously had Ubuntu 11.04 64-bit installed.  I notice a great performance difference between these two versions.  Aside from the horrible Gnome desktop in 11.10 compared to 11.04, I cannot determine why Ubuntu 11.10 performance is horrible.  I also had installed Fedora 15 64-bit for a test where Fedora 15 ran fast on this same system.  With all the negative media coverage that I have read on Ubuntu 11.10, I doubt that I will continue to use Ubuntu at this time.  I may try Ubuntu again with version 12.04 (not sure when of when it will get released).


The solution for Ubuntu 11.10 (32-bit) is to install the **ATI/AMD proprietary FGLRX graphics driver** first before installing any updates from the Update Manager.  If I install the 177 updates available in Update Manager before installing the ATI/AMD proprietary FGLRX graphics driver, then the ATI/AMD proprietary FGLRX graphics driver will ***not*** install.

---

### Post by Nipper007 on 2011-11-07
> **Nipper007 said:**
> The solution for Ubuntu 11.10 (32-bit) is to install the **ATI/AMD proprietary FGLRX graphics driver** first before installing any updates from the Update Manager.  If I install the 177 updates available in Update Manager before installing the ATI/AMD proprietary FGLRX graphics driver, then the ATI/AMD proprietary FGLRX graphics driver will ***not*** install.

When installing Ubuntu 11.10 64-bit version, the **ATI/AMD proprietary FGLRX graphics driver** will not install after initial installation.  I installed the updates from Update Manager and still the **ATI/AMD proprietary FGLRX graphics driver** will not install.  This causes a huge performance problem that I am seeing on the Sony VGN-NW250F laptop.

I installed Ubuntu 11.10 32-bit version back on the Sony VGN-NW250F laptop where the **ATI/AMD proprietary FGLRX graphics driver** install after initial installation.

---

