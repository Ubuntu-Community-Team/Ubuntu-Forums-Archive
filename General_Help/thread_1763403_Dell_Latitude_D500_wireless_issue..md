---
title: "Dell Latitude D500 wireless issue."
date: 2011-05-20
forum: General Help
---

### Post by Pontster on 2011-05-20
Hello
I've only recently started using ubuntu (10.10) and running it on a relatively old laptop. It's been working fine up until the last update when the wireless has stopped connecting. When booting up normally it connected automatically but after the update it tries a few minutes and then says it can't connect. When I look at available networks I select mine enter my key and then after a few minutes it says it can't connect. The key is correct as everything else connects fine.

I've had a look at some of the other posts where people have had similar problems but none to do with this dell model which makes me reluctant to run any of the other solutions.

I've run the lspci -v | grep -i Network command and this is what comes back.
Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04).

Can anyone help or have a solution specific to this model please?

Cheers

---

### Post by KeyserSoze93 on 2011-05-20
Did the update include a kernel update? You could try selecting the previous kernel from GRUB when the system boots (I think you have to press esc or shift to see the selection popup with GRUB2, before Ubuntu begins loading.)

---

### Post by Pontster on 2011-05-20
Should I press whichever one it is when the bios is loading?

---

