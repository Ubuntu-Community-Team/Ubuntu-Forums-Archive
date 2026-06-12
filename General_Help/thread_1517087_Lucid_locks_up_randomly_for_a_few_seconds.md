---
title: "Lucid locks up randomly for a few seconds"
date: 2010-06-24
forum: General Help
---

### Post by Dj Dutchman on 2010-06-24
Hi, I recently installed Lucid (64-bit) on a Dell laptop but I'm experiencing problems where it locks up for a few seconds and then continues, it seems to be most frequent when typing making the laptop almost unusable (On average a username/password combo causes it to lock up about 3 times). It also seems to become more and more frequent as time goes on but I've also had it lock up when trying to type my password in.

I looked at the logs and one thing popped out to me:
```
Jun 24 20:47:33 gina-laptop kernel: [  929.871341] b43-phy0: 
Jun 24 20:47:33 gina-laptop kernel: [  929.871346] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Jun 24 20:47:33 gina-laptop kernel: [  929.871355] b43-phy0: Controller RESET (DMA error) ...
Jun 24 20:47:33 gina-laptop kernel: [  929.871360] Controller restarted
Jun 24 20:47:34 gina-laptop kernel: [  930.210347] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

These lines repeatedly pop up every couple of seconds.

Anybody know what might be causing this?

---

### Post by dnguyen1963 on 2010-06-24
> **Dj Dutchman said:**
> Hi, I recently installed Lucid (64-bit) on a Dell laptop but I'm experiencing problems where it locks up for a few seconds and then continues, it seems to be most frequent when typing making the laptop almost unusable (On average a username/password combo causes it to lock up about 3 times). It also seems to become more and more frequent as time goes on but I've also had it lock up when trying to type my password in.

I looked at the logs and one thing popped out to me:
```
Jun 24 20:47:33 gina-laptop kernel: [  929.871341] b43-phy0: 
Jun 24 20:47:33 gina-laptop kernel: [  929.871346] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Jun 24 20:47:33 gina-laptop kernel: [  929.871355] b43-phy0: Controller RESET (DMA error) ...
Jun 24 20:47:33 gina-laptop kernel: [  929.871360] Controller restarted
Jun 24 20:47:34 gina-laptop kernel: [  930.210347] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

These lines repeatedly pop up every couple of seconds.

Anybody know what might be causing this?

Please search the forum before posting a new thread.  There are much info on 10.04 lock-ups.

---

### Post by Dj Dutchman on 2010-06-24
Um... next time please actually read my post. I did search for other topics with regards to my problem and most of them were concering freezes that required a hard reset. Why do I always seem to run into such problems when trying to solve my [all to regular] Ubuntu problems?

---

### Post by Dj Dutchman on 2010-06-25
Never mind, I managed to solve it myself, the problem was with the open source Broadcom B43 driver I switched to the propriety STA driver and I no longer have problems.

---

