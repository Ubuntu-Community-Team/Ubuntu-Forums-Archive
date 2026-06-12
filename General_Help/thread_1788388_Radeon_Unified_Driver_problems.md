---
title: "Radeon Unified Driver problems"
date: 2011-06-22
forum: General Help
---

### Post by Vendettaseve on 2011-06-22
Hey everyone

I just attemted the install for the Radeon unified drivers. Im running Ubuntu 10.04 with a X1200 series graphics card. > 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]


The setup seemed to go fine and I restarted as it suggested. but now when I attempt to open the new catalist control center application it gives me a message about not detecting any Radeon components or I need to configure them. Sadly this message isnt copy/pasteable.


Anyone know whats going on?

---

### Post by Mark Phelps on 2011-06-22
If these were not the default open-source drivers, then it's likely that they will NOT work with any Ubuntu version (using your card) newer than 8.10.  AMD/ATI dropped proprietary Linux driver support for your card years ago.

If you got them from AMD/ATI, they won't work.

If you got them from a ppa, can't help you there, sorry.

---

### Post by Vendettaseve on 2011-06-22
> **Mark Phelps said:**
> If these were not the default open-source drivers, then it's likely that they will NOT work with any Ubuntu version (using your card) newer than 8.10.  AMD/ATI dropped proprietary Linux driver support for your card years ago.

If you got them from AMD/ATI, they won't work.

If you got them from a ppa, can't help you there, sorry.


Funny, help.ubuntu.com seems to disagree with you on this one... Hence why I tried it. lol Has a big list of cards that it will work on, including the one Im using.

[Help.Ubuntu Unified Radeon documentation]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by khelben1979 on 2011-06-22
Mark Phelps is correct.

You have 2 choices here: 
1. Use the AMD Catalyst 9.3 (non-free driver) with an older version of Ubuntu.

2. Use the open source driver which is part of the Linux kernel, and if you're using the latest version of Ubuntu you get the best (hopefully!) graphic drivers which is part of the Linux kernel.

The latest version of Ubuntu has a version of the X server which isn't compatible with AMD Catalyst 9.3, it only works with newer versions of the Catalyst drivers which does not support your X1200 graphic card.

---

### Post by Vendettaseve on 2011-06-22
Thanks guys. Man I was so close, curse you random ubuntu help articles.


Anyways I was thinking about upgrading pretty soon anyways, the new one looks pretty handy. Just waiting to make sure everything will work with it :3

Thanks again.

V

---

