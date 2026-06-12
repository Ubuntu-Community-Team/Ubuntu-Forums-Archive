---
title: "ASM1061 SATA3 6Gbps controller drivers needed?"
date: 2012-01-06
forum: General Help
---

### Post by janmartin on 2012-01-06
Hi all,

I have a Shuttle SX58H7 Pro PC, with a SDD and a HDD connected via ASM1061 SATA3 controller at 6Gbps.

Problem is that both drives are not found when installing Ubuntu 10.04.3 or 11.10 64 bit.

Do I need to install drivers? 
If so, how?

Thanks.

---

### Post by Mugsy323 on 2012-01-22
Your motherboard's bios should detect the drives plugged into the card like any other drive, which would allow you to install Ubu to that drive.

If Ubu is not detecting the drives plugged into your card, it's not a driver issue, it's your MoBo.

(I have the same card and Ubu sees my SSD drive just fine with no added driver.)

---

### Post by janmartin on 2012-01-22
A BIOS update provided by Shuttle support solved this.

---

