---
title: "Sudden problem with Skype"
date: 2011-06-08
forum: General Help
---

### Post by Finfo on 2011-06-08
Hi There, 

I am a newbie, running Ubuntu 10.04. I have the following issue with Skype. Some time ago in order to make the web cam work properly and avoid the green screen issue I search the forum and solve the issue applying the suggested launcher in the usr/local/bin:

#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

Everything was working fine, but suddenly when I try to open Skype after logging in it crashes. I open it through a terminal and this is the output: 

/usr/local/bin/skype: line 2:  4146 Aborted     LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

As always, thank you very much for this supportive community

Finfo

---

### Post by Jouke74 on 2011-06-08
Skype has problems with it's own software together with configuration and servers. There is no connection or it logs on but crashes. They are working on a fix. 

:lolflag: Microsoft took over Skype...

---

### Post by Finfo on 2011-06-08
> **Jouke74 said:**
> Skype has problems with it's own software together with configuration and servers. There is no connection or it logs on but crashes. They are working on a fix. 

:lolflag: Microsoft took over Skype...

Thanks for your reply Jouke74. I agree with you, and soon I will look for an alternative to Skype due to its new owner. 
But my problem is that the program itself is crashing, it logs into the network but after that it closes. I believe is an issue with the launcher, but have no idea how to solve it.

---

### Post by mastablasta on 2011-06-08
this issue has been posted all over the web and there is also a solution. you will need to delete the shared.xml file in the .skype directory.
 
additionally there have really been server issues lately and it doesn't work good in MS as well. 
 
microsoft actually hasn't took it over yet ;-)
 
also i dont' know what other alternative actually exist with same quality (used to be of good quality) or lower prices.

---

### Post by Finfo on 2011-06-08
> **mastablasta said:**
> this issue has been posted all over the web and there is also a solution. you will need to delete the shared.xml file in the .skype directory.
 
additionally there have really been server issues lately and it doesn't work good in MS as well. 
 
microsoft actually hasn't took it over yet ;-)
 
also i dont' know what other alternative actually exist with same quality (used to be of good quality) or lower prices.

thank you mastablasta, I did not find that solution, probably I search in the wrong places.
Thanks for your reply,  I will search with your clue of deleting the shared file. 
Best,
Finfo

---

### Post by mastablasta on 2011-06-08
well in case you can't find it: [http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html](http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html)

---

### Post by Finfo on 2011-06-08
After my inefficient searches, I follow the suggestion and renamed the shared file. It solved the issue. 
Many thanks.

---

