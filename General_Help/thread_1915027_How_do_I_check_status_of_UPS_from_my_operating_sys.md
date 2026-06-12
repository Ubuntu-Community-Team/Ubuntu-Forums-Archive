---
title: "How do I check status of UPS from my operating system?"
date: 2012-01-25
forum: General Help
---

### Post by arroy_0209 on 2012-01-25
I am using Ubuntu 10.04LTS and am unable to check current status of the UPS using any of the menus provided in system->preferences or system->administration. Earlier I have checked UPS in the same operating system but after recent re-installation, I do not see the appropriate menu. I need to check condition of my UPS since some peculiar short duration noise is  coming out  of the UPS at times. Can anybody please suggest some way?

---

### Post by Mark Phelps on 2012-01-25
If the funny noise is a hign-pitched squeal, that most likely means your UPS is about to fail.

I had that happen on a couple of UPS's -- and fortunately, there were both less than 12 months old, so I was able to get them replaced under warranty.

---

### Post by SeijiSensei on 2012-01-25
Is it an APC?  If so, you can run [apcupsd]("https://help.ubuntu.com/community/apcupsd") to monitor the power supply and take various actions depending on its state.

---

