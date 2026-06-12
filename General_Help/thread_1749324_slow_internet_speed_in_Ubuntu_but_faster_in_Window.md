---
title: "slow internet speed in Ubuntu but faster in Windows?"
date: 2011-05-04
forum: General Help
---

### Post by nacho32 on 2011-05-04
I have a triple boot computer XP/W7/Ubuntu
speed test
Ubuntu ping 19ms 4.98 mbps down 0.87 up
    XP ping 13ms 7.90 mbps down 5.91 up
   W-7 ping 14ms 7.66 mbps down 4.80 up

netgear WG111 V3 usb adapter

any help would be great

---

### Post by nacho32 on 2011-06-20
:popcorn: fixed under connections I choose to unchecked automatic and set the MTU 1500 now it works just as fast as windows

---

### Post by sreekar1 on 2011-06-25
Well,I am facing a similar problem(i.e., some sites like cbseguess.com or wall.alphacoders.com are quite slow in delivering their content,i.e.,only their top banners on their page are visible,but their content takes an eternity to load).I was using the system monitor and I found out that the download and upload speeds peake  dramatically on starting the connection,but decreased a lot soon afterwards.I have noot observed this in my other windows computer.Some help,please?

---

### Post by dcstar on 2011-06-25
> **nacho32 said:**
> :popcorn: fixed under connections I choose to unchecked automatic and set the MTU 1500 now it works just as fast as windows

I actually have my MTU set to 1454 as that is optimum for my PPPoE ADSL connection.

1500 is ok but you still get sub-optimal packet utilisation in the underlying ATM network that ADSL can use.

---

### Post by sreekar1 on 2011-06-26
Well,the sites are still loading quite *slowly*.Any help?

---

### Post by sreekar1 on 2011-07-04
HTTPS sites like addons.mozilla.org are also loading very slowly.Why?](*,)](*,)

---

