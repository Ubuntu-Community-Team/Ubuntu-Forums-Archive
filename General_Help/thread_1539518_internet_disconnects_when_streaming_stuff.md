---
title: "internet disconnects when streaming stuff"
date: 2010-07-26
forum: General Help
---

### Post by surrealillusions on 2010-07-26
Hi all,

Got a problem when I try to stream stuff off the net, such as watching youtube, or listening to music clips. Basically, the internet just simply disconnects after a few seconds, or a minute at most after starting to stream - although it appears to be connected in the wireless icon thingymigig in the top right taskbar, eventually that goes though and says I'm disconnected.

While browsing normally, and using the net normally with messenger and looking through websites, uploading/downloading via ftp, with no videos or music streaming, the net stays on - no problems.

If I try to stream stuff from another computer running windoze 7, then these problems dont occur, the net doesn't disconnect and can stream till the end of time (or so it seems).

Why does this happen just on the Linux machine? This has only really started to happen today. A week ago everything seemed alright.
Running Ubuntu 10.04.

Thanks.

---

### Post by akvik on 2010-07-30
Hi,

I've got the same symptom with 10.04, can't recall having this problem with Karmic. Here's the kernel log: 

```

Jul 30 12:07:17 akvik-laptop kernel: [  225.256163] Registered led device: iwl-phy0::radio
Jul 30 12:07:17 akvik-laptop kernel: [  225.256247] Registered led device: iwl-phy0::assoc
Jul 30 12:07:17 akvik-laptop kernel: [  225.256286] Registered led device: iwl-phy0::RX
Jul 30 12:07:17 akvik-laptop kernel: [  225.256322] Registered led device: iwl-phy0::TX
Jul 30 12:08:15 akvik-laptop kernel: [  282.932070] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:15 akvik-laptop kernel: [  282.932080] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:15 akvik-laptop kernel: [  283.432063] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
Jul 30 12:08:16 akvik-laptop kernel: [  283.932063] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:16 akvik-laptop kernel: [  283.932073] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:16 akvik-laptop kernel: [  284.432063] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:16 akvik-laptop kernel: [  284.432073] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:17 akvik-laptop kernel: [  284.932063] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Jul 30 12:08:18 akvik-laptop kernel: [  285.756049] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Jul 30 12:08:21 akvik-laptop kernel: [  288.936053] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:21 akvik-laptop kernel: [  288.936063] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:21 akvik-laptop kernel: [  289.436055] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
Jul 30 12:08:22 akvik-laptop kernel: [  289.936045] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:22 akvik-laptop kernel: [  289.936055] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:22 akvik-laptop kernel: [  290.436071] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:22 akvik-laptop kernel: [  290.436081] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:23 akvik-laptop kernel: [  290.936080] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Jul 30 12:08:27 akvik-laptop kernel: [  294.940070] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:27 akvik-laptop kernel: [  294.940080] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:27 akvik-laptop kernel: [  295.441077] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
Jul 30 12:08:28 akvik-laptop kernel: [  295.940069] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:28 akvik-laptop kernel: [  295.940079] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:28 akvik-laptop kernel: [  296.441038] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:28 akvik-laptop kernel: [  296.441048] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:29 akvik-laptop kernel: [  296.940076] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Jul 30 12:08:33 akvik-laptop kernel: [  300.944051] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:33 akvik-laptop kernel: [  300.944062] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:33 akvik-laptop kernel: [  301.445069] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
Jul 30 12:08:34 akvik-laptop kernel: [  301.944070] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:34 akvik-laptop kernel: [  301.944080] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:34 akvik-laptop kernel: [  302.444052] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:34 akvik-laptop kernel: [  302.444062] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:35 akvik-laptop kernel: [  302.944062] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Jul 30 12:08:39 akvik-laptop kernel: [  306.948091] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:39 akvik-laptop kernel: [  306.948101] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:39 akvik-laptop kernel: [  307.448049] iwl3945 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
Jul 30 12:08:40 akvik-laptop kernel: [  307.948059] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:40 akvik-laptop kernel: [  307.948070] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:40 akvik-laptop kernel: [  308.448063] iwl3945 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
Jul 30 12:08:40 akvik-laptop kernel: [  308.448073] iwl3945 0000:03:00.0: Error setting new configuration (-110).
Jul 30 12:08:41 akvik-laptop kernel: [  308.948053] iwl3945 0000:03:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
Jul 30 12:08:42 akvik-laptop kernel: [  309.788048] iwl3945 0000:03:00.0: No space for Tx
Jul 30 12:08:42 akvik-laptop kernel: [  309.788059] iwl3945 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
Jul 30 12:08:42 akvik-laptop kernel: [  309.788066] iwl3945 0000:03:00.0: Error setting new configuration (-28).
Jul 30 12:08:42 akvik-laptop kernel: [  309.788075] iwl3945 0000:03:00.0: No space for Tx
Jul 30 12:08:42 akvik-laptop kernel: [  309.788080] iwl3945 0000:03:00.0: Error sending REPLY_LEDS_CMD: enqueue_hcmd failed: -28


```

---

### Post by Ev1L on 2010-08-02
same here

---

### Post by laialexander on 2010-08-07
Yes, also have the same problem, WiFi disconnected when computer has heavy connectivity to the network... What I have to do was to turn off the hardware wireless key and turn it on again.  My computer is IBM T60 with iwl3945 I think.  Thanks.

---

