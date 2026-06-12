---
title: "linux source code"
date: 2009-09-15
forum: General Help
---

### Post by mas123 on 2009-09-15
Hi all, 

I want to access one item from the linux source code? Particularly i am looking for rtc.c. Where should I find such files. 

Thanks in advance,

---

### Post by rocket16 on 2009-09-15
Hello friend. Go to /usr/src, and then, if you do not find the Source Code you need, then use the "locate" command in Terminal to find your need.

---

### Post by mas123 on 2009-09-15
That folder contains only header files. 

I tried locate rtc.c but no luck

---

### Post by lisati on 2009-09-15
Google is your friend:

[s]
[http://ccrma.stanford.edu/courses/250a-fall-2002/docs/avrlib/rtc_8c.html](http://ccrma.stanford.edu/courses/250a-fall-2002/docs/avrlib/rtc_8c.html)
[http://ccrma.stanford.edu/courses/250a-fall-2002/docs/avrlib/rtc_8c-source.html](http://ccrma.stanford.edu/courses/250a-fall-2002/docs/avrlib/rtc_8c-source.html)
[http://www.koders.com/c/fid57CBFD93ED3442F2F39B573A68F44DB07D8EB827.aspx](http://www.koders.com/c/fid57CBFD93ED3442F2F39B573A68F44DB07D8EB827.aspx)
[/s]
[http://www.gelato.unsw.edu.au/lxr/source/drivers/char/s3c2410-rtc.c](http://www.gelato.unsw.edu.au/lxr/source/drivers/char/s3c2410-rtc.c)

---

### Post by sunchiqua on 2009-09-15
Source code of rtc.c: _[http://www.codase.com/search/display?file=L2dlbnRvbzIvdmFyL3RtcC9yZXBvcy9jb2Rhc2UuYy9saW51eC0yLjYuMTIvZHJpdmVycy9jaGFyL3MzYzI0MTAtcnRjLmM=&lang=c](http://www.codase.com/search/display?file=L2dlbnRvbzIvdmFyL3RtcC9yZXBvcy9jb2Rhc2UuYy9saW51eC0yLjYuMTIvZHJpdmVycy9jaGFyL3MzYzI0MTAtcnRjLmM=&lang=c)_

---

### Post by sisco311 on 2009-09-15
you can download the source code if you wish. it's ~80MB:
```
cd /usr/src
sudo apt-get source linux-image-$(uname -r)
find ./ -name "rtc.c"
```

---

