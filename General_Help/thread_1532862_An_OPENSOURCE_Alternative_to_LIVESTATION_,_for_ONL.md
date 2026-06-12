---
title: "An OPENSOURCE Alternative to LIVESTATION , for ONLINE TV with mplayer?"
date: 2010-07-17
forum: General Help
---

### Post by frenchn00b on 2010-07-17
LIVESTATION is not opensource

Could someone make a PERL or PYTHON script taht let us what TV using mplayer, there is some links:

[http://www.paisawaisa.com/community/livetv/](http://www.paisawaisa.com/community/livetv/)

[http://favchannels.com/watch-tv-live-online/](http://favchannels.com/watch-tv-live-online/)
[http://wwitv.com](http://wwitv.com)
[http://www.techtalkz.com/linux-opensource/167120-ubuntu-7-04-streaming.html](http://www.techtalkz.com/linux-opensource/167120-ubuntu-7-04-streaming.html)


[http://www.murga-linux.com/puppy/viewtopic.php?t=39445&start=45&sid=5fe7bc25aea3d6ab97a341dc30bdf59f](http://www.murga-linux.com/puppy/viewtopic.php?t=39445&start=45&sid=5fe7bc25aea3d6ab97a341dc30bdf59f)

---- 

Please find a web tv online (free and opensource) program:
**How to use it?**
> cd ; tar xvpfz   pupwebtv-ubuntu.tar.gz  
cd ; mkdir  .PupWebTV ; cp pupwebtv/channels.txt .PupWebTV 
cd ; cd pupwebtv ;  ./PupWebTV

---

### Post by afrodeity on 2010-10-16
```
tar xvpfz pupwebtv-ubuntu.tar.gz 

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

```

---

### Post by afrodeity on 2011-04-06
Still wondering if there is an opensource alternative to Livestation or equivalent?

---

### Post by frenchn00b on 2011-04-06
> **afrodeity said:**
> Still wondering if there is an opensource alternative to Livestation or equivalent?

Sure there are my solution and friend's solution:

- [http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v50.1%5D?content=127893&PHPSESSID=b7ec731360baa55b05d3e0b343a855b8](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v50.1%5D?content=127893&PHPSESSID=b7ec731360baa55b05d3e0b343a855b8)

- and the program own made by johnsie: [http://ubuntuforums.org/member.php?u=44267](http://ubuntuforums.org/member.php?u=44267)

---

### Post by oldos2er on 2011-04-06
Here's one example using rtmpdump with Aljazeera tv: ```
rtmpdump -v -r rtmp://livestfslivefs.fplive.net/livestfslive-live/ -y "aljazeera_en_veryhigh?videoId=747084146001&lineUpId=&pubId=665003303001&playerId=751182905001&affiliateId=" -W "http://admin.brightcove.com/viewer/us1.24.04.08.2011-01-14072625/federatedVideoUI/BrightcovePlayer.swf \
-p "http://english.aljazeera.net/watch_now/ -a "aljazeeraflashlive-live?videoId=747084146001&lineUpId=&pubId=665003303001&playerId=751182905001&affiliateId=" | mplayer -
```

---

### Post by afrodeity on 2011-04-06
> **oldos2er said:**
> Here's one example using rtmpdump with Aljazeera tv: ```
rtmpdump -v -r rtmp://livestfslivefs.fplive.net/livestfslive-live/ -y "aljazeera_en_veryhigh?videoId=747084146001&lineUpId=&pubId=665003303001&playerId=751182905001&affiliateId=" -W "http://admin.brightcove.com/viewer/us1.24.04.08.2011-01-14072625/federatedVideoUI/BrightcovePlayer.swf \
-p "http://english.aljazeera.net/watch_now/ -a "aljazeeraflashlive-live?videoId=747084146001&lineUpId=&pubId=665003303001&playerId=751182905001&affiliateId=" | mplayer -
```

Forgot about rtmdump thanks.:popcorn:

---

