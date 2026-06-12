---
title: "How to adb push in ubuntu 11.04?"
date: 2011-10-08
forum: General Help
---

### Post by Phaze08 on 2011-10-08
*SOLVED*



Ok, so I've been working on setting up adb for quite a while, I hear its very useful and I've also heard it helps for android theming, which I'm about to start learning. So, I got up to the point where it recognizes my device and everything seems to be good.
When I go to push a file to the phone, I type './adb shell' and then it goes to the next line and has a #. So I tell it to push the file and then I get '/sbin/sh: adb: not found'
What am I doing wrong? Have I not set up something right? 

In case anyone was wondering, this is what I typed to push the file, I think its right. 
~ # ./adb push /downloads/bootanimation.zip system/media bootanimation.zip
Then it said:
/sbin/sh: ./adb: not found
~ #  push /downloads/bootanimation.zip system/media bootanimation.zip     
/sbin/sh: push: not found
~ # adb push /downloads/bootanimation.zip system/media bootanimation.zip  
/sbin/sh: adb: not found
~ # adb push bootanimation.zip system/media                             
/sbin/sh: adb: not found

If anyone knows about this, it would be awesome. I know a few people who can help possibly but their not available to contact for a while and would like to not have to ask them something for once lol. Thanks in advance. :D

---

