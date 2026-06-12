---
title: "System start lagging every 30 seconds"
date: 2010-09-22
forum: General Help
---

### Post by Christian Knudsen on 2010-09-22
I'm currently experiencing that my system lags for a few seconds every 30 seconds or so. Checking my log, there's hundreds of the same error message:

> Sep 22 21:46:30 christian-laptop kernel: [ 6529.349318] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:30 christian-laptop kernel: [ 6529.349323] ath9k: Unable to reset channel (5620 Mhz) reset status -5
Sep 22 21:46:30 christian-laptop kernel: [ 6529.349347] ath9k: Unable to set channel
Sep 22 21:46:30 christian-laptop kernel: [ 6529.623071] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:30 christian-laptop kernel: [ 6529.623077] ath9k: Unable to reset channel (5640 Mhz) reset status -5
Sep 22 21:46:30 christian-laptop kernel: [ 6529.623098] ath9k: Unable to set channel
Sep 22 21:46:31 christian-laptop kernel: [ 6529.873209] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:31 christian-laptop kernel: [ 6529.873215] ath9k: Unable to reset channel (5660 Mhz) reset status -5
Sep 22 21:46:31 christian-laptop kernel: [ 6529.873236] ath9k: Unable to set channel
Sep 22 21:46:31 christian-laptop kernel: [ 6530.113660] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:31 christian-laptop kernel: [ 6530.113665] ath9k: Unable to reset channel (5680 Mhz) reset status -5
Sep 22 21:46:31 christian-laptop kernel: [ 6530.113686] ath9k: Unable to set channel
Sep 22 21:46:31 christian-laptop kernel: [ 6530.353278] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:31 christian-laptop kernel: [ 6530.353283] ath9k: Unable to reset channel (5700 Mhz) reset status -5
Sep 22 21:46:31 christian-laptop kernel: [ 6530.353307] ath9k: Unable to set channel
Sep 22 21:46:31 christian-laptop kernel: [ 6530.594298] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:31 christian-laptop kernel: [ 6530.594306] ath9k: Unable to reset channel (5745 Mhz) reset status -5
Sep 22 21:46:31 christian-laptop kernel: [ 6530.594495] ath9k: Unable to set channel
Sep 22 21:46:31 christian-laptop kernel: [ 6530.833486] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:31 christian-laptop kernel: [ 6530.833491] ath9k: Unable to reset channel (5765 Mhz) reset status -5
Sep 22 21:46:31 christian-laptop kernel: [ 6530.833510] ath9k: Unable to set channel
Sep 22 21:46:31 christian-laptop kernel: [ 6531.094060] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:31 christian-laptop kernel: [ 6531.094066] ath9k: Unable to reset channel (5785 Mhz) reset status -5
Sep 22 21:46:31 christian-laptop kernel: [ 6531.094137] ath9k: Unable to set channel
Sep 22 21:46:32 christian-laptop kernel: [ 6531.352451] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:32 christian-laptop kernel: [ 6531.352457] ath9k: Unable to reset channel (5805 Mhz) reset status -5
Sep 22 21:46:32 christian-laptop kernel: [ 6531.352477] ath9k: Unable to set channel
Sep 22 21:46:32 christian-laptop kernel: [ 6531.594507] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:32 christian-laptop kernel: [ 6531.594513] ath9k: Unable to reset channel (5825 Mhz) reset status -5
Sep 22 21:46:32 christian-laptop kernel: [ 6531.594696] ath9k: Unable to set channel
Sep 22 21:46:32 christian-laptop kernel: [ 6531.840426] ath9k: timeout (100000 us) on reg 0x9860: 0x00049d19 & 0x00000001 != 0x00000000
Sep 22 21:46:32 christian-laptop kernel: [ 6531.840431] ath9k: Unable to reset channel (2412 Mhz) reset status -5
Sep 22 21:46:32 christian-laptop kernel: [ 6531.840456] ath9k: Unable to set channel

Anybody know what this is?

EDIT: I'm guessing it has to do with my wireless. I had the same problem some months ago and posted here without any replies. So I just decided to use my ethernet instead. That's been working fine for a couple of months, but now it just decided to act up again for no reason I can tell, despite the fact I'm still using the ethernet and not the wireless. I've made no updates and installed no new programs.

---

