---
title: "Natty fails to boot"
date: 2011-04-29
forum: General Help
---

### Post by hhoyt on 2011-04-29
Thought I better document this, tho I fail to understand a lot of it ;-)

Install ATI 11.4 support as I am Dell inspiron 570i
lspci:
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]

Boot failure.

Add 'single' to bootmenu to come up in recovery mode and then boot low graphics. I am then told something to the effect 'hardware does not support unity' and told to switch (happily) to classic.

This fixed it. I have run unity w/o trouble w/o the ati 11.4 so suspect it was the culprit.

FYI, Howard

---

