---
title: "Need EEE Box 202/LTSP tutorial"
date: 2010-10-13
forum: General Help
---

### Post by gate array on 2010-10-13
Hi all,

I've been struggling to get an Asus EEE Box 202 to boot under an Ubuntu server. It gets the first dhcp transaction for the pxe networking but not the second to establish full tcp/ip and there the boot stops at the three-segmented ring.

At first I thought this was a video issue but some chat on #ltsp showed it was network failure because the proper driver was not in the kernel or the initrd image. There's a bunch of tutorials to get the driver in there, I've  tried four or five but none work. Can anyone tell me exactly what driver this box needs and how to get it into the initrd delivered to the clients?

fwiw, I have tried karmic, lucid and karmic upgraded to lucid to see if the module used to be there but was then dropped. I've also tried server and desktop on the server to see if desktop might have had a different mix of modules to support a broader range of hardware. I'm out of ideas and energy.

thx,

rl

---

