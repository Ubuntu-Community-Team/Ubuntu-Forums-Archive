---
title: "I think I may have some driver issues."
date: 2012-10-05
forum: General Help
---

### Post by cammy511 on 2012-10-05
I decided to try Ubuntu on my notebook. I really like it but it's rather slow and even the propriety drivers that Ubuntu installed did not help. My wireless connection goes out frequently and the system it's self is being very slow. It seems like the drivers are not getting along. 

Specs 

Hp Pavilion dm1

4 GB of ram 
AMD E 450 dual core. 2.0 GHZ 
600 GB Hard Drive 

Installed is Ubuntu 12.04

---

### Post by jerrrys on 2012-10-05
Hi cammy511, welcome to the forums  :)

I really don't know anything about AMD Radeon HD 6310, but got some forum hits.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=AMD+Radeon+HD+6310&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=AMD+Radeon+HD+6310&as_qdr=all&sa=Google+Search&lang=en)

Hope that helps

---

### Post by daslinkard on 2012-10-06
You should be able to get squared away with the following:


  Install the [proprietary one]("http://tuxcanfly.appspot.com/tag/ubuntu-broadcom-4313-43xx-bcmwl") from Broadcom.
  

Then blacklist in */etc/modprob.d/blacklist.conf*
  ```
blacklist bcm43xx  
blacklist brcmsmac   
blacklist bcma    
blacklist b43    
blacklist ssb
```   Restart and check that: 
  ```
lspci -k | grep  wl
```   Hope it works for you.

---

