---
title: "Electric Sheep Error In Lucid"
date: 2010-05-02
forum: General Help
---

### Post by Precipitous on 2010-05-02
I just installed Electric Sheep (version  2.7~b12+svn20091224-1ubuntu1) on my Ubuntu Lucid box. When I test the connection in the Preferences window, everything checks out fine, but when I try to run it from the terminal I  get the following error:
 
electricsheep: /usr/lib/i686/cmov/libavcodec.so.52: no version  information available (required by electricsheep) electricsheep: /usr/lib/i686/cmov/libavformat.so.52: no version  information available (required by electricsheep) electricsheep: relocation error: electricsheep: symbol av_init_packet,  version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link  time reference Terminated. 

If I try to preview it using System > Preferences > Screensavers, I get  a blank screen. Help!

---

### Post by eris23 on 2010-06-03
electricsheep 2.7~b12+svn20091224-1ubuntu1

[avi @ 0xae6050]max_analyze_duration reached
electricsheep: relocation error: electricsheep: symbol av_init_packet, version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link time reference

---

### Post by Precipitous on 2010-06-04
> **Precipitous said:**
> I just installed Electric Sheep (version  2.7~b12+svn20091224-1ubuntu1) on my Ubuntu Lucid box. When I test the connection in the Preferences window, everything checks out fine, but when I try to run it from the terminal I  get the following error:
 
electricsheep: /usr/lib/i686/cmov/libavcodec.so.52: no version  information available (required by electricsheep) electricsheep: /usr/lib/i686/cmov/libavformat.so.52: no version  information available (required by electricsheep) electricsheep: relocation error: electricsheep: symbol av_init_packet,  version LIBAVFORMAT_52 not defined in file libavformat.so.52 with link  time reference Terminated. 

If I try to preview it using System > Preferences > Screensavers, I get  a blank screen. Help!

I bought a larger drive, so I ended up re-installing Lucid from scratch...  Installed Electric Sheep from Synaptic, and the "configure screen-saver" script from the Electric Sheep home page. Now everything works perfectly!

I am assuming that the previous errors were caused by a conflict with something I had installed who knows when?

---

