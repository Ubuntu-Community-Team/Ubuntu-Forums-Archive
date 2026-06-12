---
title: "Unable to play DVDs"
date: 2010-05-09
forum: General Help
---

### Post by Lovefist233 on 2010-05-09
VLC console output is as follows:

```
libdvdnav: DVD Title: P9017DVD
libdvdnav: DVD Serial Number: 2b53a395
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/dai/.dvdnav/P9017DVD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
[0x7f35f400b238] main input error: ES_OUT_RESET_PCR called
[0x7f35f400b238] main input error: ES_OUT_RESET_PCR called
[0x7f35f400b238] main input error: ES_OUT_RESET_PCR called
[0x7f35f400b238] main input error: ES_OUT_RESET_PCR called
```

I have the restricted extras installed, I have to assume that libdvdcss is with them because it reports as unavailable through apt-get.  I'm new to Ubuntu, in Fedora I would do
```
yum -y install vlc libdvdcss
```
and that would be all I needed.  Here I am unsure of what to do.

---

### Post by bananas4370 on 2010-05-09
You'll need to install libdvdcss by doing the following

sudo /usr/share/doc/libdvdread4/install-css.sh

Refer to [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Hope this helps.

---

### Post by howefield on 2010-05-09
You can get libdvdcss2 from Medibuntu, either by adding the repository details to your sources list, or by downloading the .deb file from the Medibuntu packages site.

Details here...

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by Lovefist233 on 2010-05-09
So I installed libdvdcss2 as per your instructions (thanks guys) and now I get this:

```


VLC media player 1.0.6 Goldeneye
[0xa264b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: P9017DVD
libdvdnav: DVD Serial Number: 2b53a395
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/dai/.dvdnav/P9017DVD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000130
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001dd2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000264de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0030c85c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003bce00
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
[0x7f7c0c003188] main input error: ES_OUT_RESET_PCR called
[0x7f7c0c003188] main input error: ES_OUT_RESET_PCR called
[0x7f7c0c003188] main input error: ES_OUT_RESET_PCR called
[0x7f7c0c003188] main input error: ES_OUT_RESET_PCR called

```

Any ideas?

---

### Post by bananas4370 on 2010-05-09
> **Lovefist233 said:**
> So I installed libdvdcss2 as per your instructions (thanks guys) and now I get this:

```


VLC media player 1.0.6 Goldeneye
[0xa264b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3

Snip


```

Any ideas?

Does this happen with any DVD you play? Does this happen using another player? 

Cheers

---

### Post by Lovefist233 on 2010-05-09
It was with any DVD but since a reboot its all good now.

I suppose I'm just not used to having to reboot in order to see changes take effect.  Thanks for all the help guys, seems it did work out in the end.

---

### Post by bananas4370 on 2010-05-09
> **Lovefist233 said:**
> It was with any DVD but since a reboot its all good now.

I suppose I'm just not used to having to reboot in order to see changes take effect.  Thanks for all the help guys, seems it did work out in the end.

Good to know it's all working now.

Cheers
Patrick

---

