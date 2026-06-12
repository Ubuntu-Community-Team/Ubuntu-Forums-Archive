---
title: "Hotmal won't link with Evolution?"
date: 2010-10-09
forum: General Help
---

### Post by Car.Golden7 on 2010-10-09
I've been working on trying to link my Hotmail account to Evolution. so that my hotmail inbox will show up on Evolution, you know?
So far I've tried this method: [http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)
and failed at the "good stuff"part with an error message in the Terminal **E: couldn't find package hotway**

I've also tried the method of changing my servers to pop3 and smpt.live.com and whatnot, but still I am having trouble. Anyone able to help me out?

---

### Post by M4he on 2010-10-09
If it's Live Mail you mean with hotmail then you can easily access it via pop3.
just put in > pop3.live.com:995 as receive server and choose **SSL/TLS**

put in > smtp.live.com:587 as send server and choose **TLS**

put in your mail address as user name for both. (send server needs authentication too)

---

