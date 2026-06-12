---
title: "Strange Samba behaviour in 10.04"
date: 2010-09-03
forum: General Help
---

### Post by qmanol on 2010-09-03
I've just installed 10.04 on an Intel D945GCLF2 on a Seagate ST32000542AS 2TB drive. I had to format the drive MBR since the board won't boot off GPT devices, but now I'm having some interesting behaviour with samba.

I have shares on the ubuntu machine, and when copying from the share to my win7 64-bit desktop, the transfer rate is fairly steady, and hits 350mbps or more. When copying to the share, however, the connection starts at ~500mbs, then after about 10 seconds drops to nothing for ~3 seconds, then jumps up for a second, stalls again, and continues this behaviour. The HDD light on the system continues at all times, so it seems as if the samba service is allowing the connection to overwhelm the buffer, and then having to pause while the disk catches up.

Is there anything else that might cause this behaviour, and is there anything I can do? I've already changed the samba socket options to TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192, and I just set up the shares using nautilus.

---

