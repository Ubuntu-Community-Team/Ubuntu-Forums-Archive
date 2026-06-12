---
title: "Memlock &amp; raw1394?"
date: 2010-02-05
forum: General Help
---

### Post by connor4312 on 2010-02-05
Hi,

I recently upgraded my Ubuntu 9.10 install into an Ubuntu Studio one, and I was poking around the new stuff, and came across "Enable Memlock", "Enable nice" and "Enable raw139 Access" I've Googled these, but have come up with nothing explaining *what* they are. Any help? And what are the pros and cons on anabling these?

Thanks,
Connor

---

### Post by cchhrriiss121212 on 2010-02-08
Raw 1394 allows you to use firewire/1394 devices
Memlock gives audio programs access to as much memory as you define (100% recommended for audio production)
nice gives audio programs priority over other things that are running.

Further reading here: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

You need all these to use low latency sound work on your system which is why they are listed in Ubuntu studio controls.

---

