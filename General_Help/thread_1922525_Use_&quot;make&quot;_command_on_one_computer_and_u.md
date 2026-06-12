---
title: "Use &quot;make&quot; command on one computer and use &quot;make install&quot; on the other"
date: 2012-02-09
forum: General Help
---

### Post by krtzer on 2012-02-09
Hello everyone, I was wondering if it is possible to use the "make" command to build files on a flash drive using one system and then use the "make install" commands on another system to install the made files. 

The reason why I ask this is because I am installing OpenCV to a bealgeboard (that is running an arm core disto of ubuntu) but it takes forever to compile the files since it only has a 1Ghz processor. I was wondering if there was some way to expedite this process by extract the tar file to a usb stick and then use my laptop's processing power to compile the files and then install them to the beagleboard. 

I do not know how make works, so an explanation of what it does would help. 

Thanks.

---

### Post by Cheesemill on 2012-02-09
It is possible, but it's quite involved, it's called 'cross compiling'.
I've never done it myself so I can only tell you what to search for.

If you Google for 'opencv cross compiling' you should get some usefull results.

---

