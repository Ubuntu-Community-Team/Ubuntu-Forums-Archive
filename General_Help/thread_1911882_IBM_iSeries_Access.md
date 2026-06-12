---
title: "IBM iSeries Access"
date: 2012-01-19
forum: General Help
---

### Post by gypsumwolf on 2012-01-19
Ive mostly followed these instructions:  
[http://www.allars.co.uk/2011/06/installing-ibm-iseries-access-on-ubuntu-11-04/]("http://www.allars.co.uk/2011/06/installing-ibm-iseries-access-on-ubuntu-11-04/")

Lubuntu 11.10 is the base system.

I can run the ibm5250, but when I run the setup5250, I get this error:
```
Linux# /opt/ibm/iSeriesAccess/bin/setup5250 -LANGID en_us
setup5250: [ INFORMATIONAL ]: Build Date: March 2008 (1.6)
setup5250: [ INFORMATIONAL ]: /opt/ibm/iSeriesAccess/bin/setup5250 -LANGID en_us 
setup5250: [ ERROR ]: Xt Warning: locale not supported by C library, locale unchanged.
setup5250: [ ERROR ]: Xt Warning: Missing charsets in String to FontSet conversion.
Segmentation fault
Linux#
```

---

### Post by gypsumwolf on 2012-01-20
Solved. needed to do:

locale-gen en_US

---

