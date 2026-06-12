---
title: "Webcam won't work in Google Talk (Gmail), but works in Skype"
date: 2011-07-08
forum: General Help
---

### Post by dt_ on 2011-07-08
Hi all,

I have an interesting problem going here with my webcam. In Skype, I have absolutely zero problems using my webcam. I've got a Dell Inspiron 1525 running Ubuntu 11.04 (64-bit), fully updated.
However, when I use the Google talk plugin in my browser (tried both Firefox 5 and Chrome 12), when I verify my settings or try to chat, my webcam doesn't work. The blue LED next to my webcam lights up, indicating it's powered up, but no video is displayed. The microphone works just fine however. Why is this? I made sure I have the latest update to the Google plugin but even though it shows "Laptop Integrated Webcam" as selected, it doesn't display video.
 :/

Any help would be much appreciated here.

Thanks!
dt

** EDIT: That was fast.. I found a fix! **
I followed the instructions posted by Video Chat Eng. Blue [here](http://www.google.com/support/forum/p/chat/thread?tid=4fea321dbee2fb81&hl=en) and then I did the chmod a+x and chmod o+x on the resulting GoogleTalkPlugin script. Worked like a charm :)

---

### Post by bhishan on 2011-08-24
For me, the webcam works but the microphone doesn't work?

---

