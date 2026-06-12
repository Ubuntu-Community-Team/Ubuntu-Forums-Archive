---
title: "lost higher resolutions"
date: 2010-04-30
forum: General Help
---

### Post by fm1234 on 2010-04-30
Hi,

somehow I lost the higher resolutions for my computer. The highest available is 1360x768 (which doesn't work well) and currently I'm using 1024x768. Before, I had 1280x1024 working well and I even had higher resolutions available in nvidia-settings.

I've ubuntu 9.10 with nvidia drivers (185.18.36).

I've read [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution), but not necessarily all of it or understood all of it.

I've tried dpkg-reconfigure xserver-xorg and the xrandr stuff but nothing has changed, except what xrandr reports, regarding the addition of two modelines 1280x1024.

In the end, I suppose something has corrupted some file but how can I figure it out?

```

Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1280 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
   1280x1024_72.00   71.9  
  1280x1024_60.00 (0x15c)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

```

---

### Post by fm1234 on 2010-04-30
I just realised that dpkg-reconfigure xserver-xorg should be asking some questions but in fact nothing happens.

What can I do?

---

