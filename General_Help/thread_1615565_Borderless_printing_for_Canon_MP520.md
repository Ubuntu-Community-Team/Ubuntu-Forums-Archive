---
title: "Borderless printing for Canon MP520"
date: 2010-11-07
forum: General Help
---

### Post by voyler on 2010-11-07
Hello everyone, this is my first post to this excellent forum.

My father in law is running ubuntu on his computer together with a Canon MP 520 printer. He wanted to make borderless printouts, but this is not possible with the current driver from Canon. Instead I modified the driver and enabled this function. It works perfectly. Now, I did spend hours looking for such a modified driver and never found any, except from others looking for the same. Well, here it is.


Instructions for install:

(re)place: **cifmp520.conf** in **/usr/lib/bjlib/**

and let

**Canon-MP520-series.ppd** replace the canon ppd file in   **/etc/cups/ppd**


I was using Nautilus to do it: **sudo nautilus** in command line

Good luck!


I am natively not a linux person, but I do recognize the pure brilliance  of the open source community - on behalf of my father in law - thank  you! Who knows, one day I might migrate to linux myself.

By the way, I found that the linux driver has been crippled by Canon, so I also made another version - enabling all the functions - not only borderless printing - that you normally find in the driver for windows. If anyone is interested I may also attach that one, but my father in law was not interested :P

---

