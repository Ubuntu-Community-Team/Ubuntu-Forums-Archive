---
title: "Quick Help Please?"
date: 2010-12-11
forum: General Help
---

### Post by thelonelywind on 2010-12-11
Ok, so the other day my usb died and went to heaven. Boom, happens everyday to lots of people. Problem is that means I can't install Ubuntu because my CD drive is also dead! :'( So naturally being a lover of Ubuntu I looked for alternate ways to install which led me to think about the way Ubuntu had loaded from the Usb. I wondered if I could use a small partition on my drive as a holder for the Ubuntu ISO files and using Neogrub (which I had installed to the Windows Boot Menu using EasyBCD)if I could load the Kernel, and Module and boot from that partition (further Googling confirmed this works and is 100% possible) So this is what I end up with... 

root=(hd0,2)
kernel /casper/vmlinuz
module /??????/??????
boot


So my problem is, where do I locate the module file in the Ubuntu ISO files I put on the partition? Or if I'm just doing it plain wrong help me out please! :KS

---

