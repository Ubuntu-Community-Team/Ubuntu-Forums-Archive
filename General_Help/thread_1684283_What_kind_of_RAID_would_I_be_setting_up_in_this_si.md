---
title: "What kind of RAID would I be setting up in this situation?"
date: 2011-02-08
forum: General Help
---

### Post by frotzed on 2011-02-08
Fairly basic question.  I'd like to set up Ubuntu 10.10 on my PC with two HDD's in a RAID 1 array.  My MoBo has 6 SATA ports hardwired to the board (2 are used by devices, 1 by the current HDD).

So, if I get 2 HDD's and connect them to the MoBo via SATA - assuming I get them into the correct port on the MoBo etc - would I then be looking to set up a software RAID, hardware raid or fake RAID?

I assume I wouldn't be dealing with a hardware RAID because I'm not connecting the HDD's into a separate RAID controller card.  But would I then just be simply setting up a fake RAID?

I've set up simple RAID 1's with Windows and Intel Matrix Software before, but this will be my first foray into RAID with Ubuntu so a shove in the right direction would be helpful.

---

### Post by dcstar on 2011-02-08
> **frotzed said:**
> Fairly basic question.  I'd like to set up Ubuntu 10.10 on my PC with two HDD's in a RAID 1 array.  My MoBo has 6 SATA ports hardwired to the board (2 are used by devices, 1 by the current HDD).

So, if I get 2 HDD's and connect them to the MoBo via SATA - assuming I get them into the correct port on the MoBo etc - would I then be looking to set up a software RAID, hardware raid or fake RAID?

I assume I wouldn't be dealing with a hardware RAID because I'm not connecting the HDD's into a separate RAID controller card.  But would I then just be simply setting up a fake RAID?

I've set up simple RAID 1's with Windows and Intel Matrix Software before, but this will be my first foray into RAID with Ubuntu so a shove in the right direction would be helpful.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by frotzed on 2011-02-09
Thanks, exactly what I was looking for.

---

