---
title: "rTorrent is constantly crashing on Ubuntu 10.04 Server"
date: 2012-02-21
forum: General Help
---

### Post by armkbdotcom on 2012-02-21
rTorrent is constantly crashing after several minutes of launching:

[B]Caught Bus error, dumping stack:
0 rtorrent() [0x4267ff]
1 rtorrent() [0x42d42f]
2 rtorrent() [0x42cf87]
3 rtorrent() [0x42c749]
4 rtorrent() [0x42b4a5]
5 rtorrent() [0x482ef6]
6 rtorrent() [0x483b4a]
7 /lib/libc.so.6(+0x33af0) [0x7fc534fabaf0]
8 /lib/libcrypto.so.0.9.8(sha1_block_data_order+0x30) [0x7fc533d53ff0]
A bus error probably means you ran out of diskspace.[/B]

Certainly I have much diskspace.

I thought maybe HDD or RAM causing this, but after thorough diagnostics and tests they are perfectly fine. Moreoever, I've tried 0.9.0 and recently 0.8.9 along with Pyroscope with same result.

Sorry for posting this here, bu maybe someone already met this issue...

---

### Post by mastablasta on 2012-02-21
perhaps where it is downloading there is not enough space or it doesn't have permission to write in that place.
 
have you tried any other torrent programmes to see what happens (such as transmission, deluge, ktorrent)?

---

### Post by elliotbeken on 2012-02-21
> have you tried any other torrent programmes to see what happens (such as transmission, deluge, ktorrent)? 	

as armkbdotcom is using ubuntu server i assume it is CLI (no GUI) interface so this wont be possible. 

Have you tried to un-install the application / purge it and install it again ~??

---

### Post by armkbdotcom on 2012-02-21
> **elliotbeken said:**
> as armkbdotcom is using ubuntu server i assume it is CLI (no GUI) interface so this wont be possible. 

Have you tried to un-install the application / purge it and install it again ~??

Yes. I've tried fresh installation, but with my existing session data. I suspect something wrong with my session data. Any way I can validate it? I guess it's too specific question to which only rtorrent/pyroscope devs can answer...

---

