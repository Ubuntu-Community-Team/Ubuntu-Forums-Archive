---
title: "Unable to get 5.1 running"
date: 2011-05-07
forum: General Help
---

### Post by Liudwik on 2011-05-07
Good day, Everyone,

I have intel HDA soundcard with ALC662 chipset on it. In ubuntu 10.10 I used to enable 5.1 sound by typing 'alsamixer' in terminal and changing number of channels from 2 to 6.

Well, in 11.04 there is no such option any more. 

I tried to change /etc/pulse/daemon.conf enabling 6 channel as default - no change. I have tried some more suggestions, but unlucky....

Please, help me solving this problem
----------------------------
the problem was upgrade to newest kernel (2.6.38-9 ).
- reinstalled system (kernel 2.6.38-8 )
- alsamixer has channel option again

---

