---
title: "Ati trifire problems"
date: 2011-05-25
forum: General Help
---

### Post by jakrzys on 2011-05-25
Hi all
configuration: ubuntu 10.10, catalyst 11.5, mainboard DFI lanparty 790FX, athlon 3200+ 2xHD5870 1xHD5850 i can't run trifire, work only crossfire, any help?

aticonfig --lsa
* 0. 01:00.0 ATI Radeon HD 5800 Series
1. 02:00.0 ATI Radeon HD 5800 Series
2. 04:00.0 ATI Radeon HD 5800 Series


aticonfig --lscc
Master adapter: 0. 01:00.0 ATI Radeon HD 5800 Series
**Candidates: 2. 04:00.0 ATI Radeon HD 5800 Series**


aticonfig --adapter=0,1,2 --cfa
CrossFire chain added


aticonfig --adapter=0 --cf=on
CrossFire chain(s) enabled
**CrossFire does not support on this platform**


CrossFire chain for adapter 0, status: enabled
0. 01:00.0 ATI Radeon HD 5800 Series
1. 02:00.0 ATI Radeon HD 5800 Series
2. 04:00.0 ATI Radeon HD 5800 Series


aticonfig --lscs
Candidate Combination:
Master: 1:0:0
Slave: 4:0:0
CrossFire is enabled on current device
CrossFire Diagnostics:
There is CrossFire Side port connection between GPUs
CrossFire can work with P2P write through peer aperture
Dongle Capabilities: support PASSTHROUGH |INTERLINK_SW_AFR | INTERLINK_AUTO_AFR | INTERLINK_BLACKING | INTERLINK_SUPERAA

---

