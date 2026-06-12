---
title: "kernel - gdl_indexer general protection segfault error 0 and 4 with libc-2.10.1.so"
date: 2010-05-03
forum: General Help
---

### Post by trinaryouroboros on 2010-05-03
Just kind of hoping for a direction here, my desktop has been dist-upgraded since Intrepid, and I was not planning on making the Lucid Lynx leap from Karmic for a little while, as I'm swamped presently, and was just considering a full wipe anyway when I have the time available to do it.

This message appeared in my /var/log/messages suddenly, and dominates it entirely, any input is highly appreciated - just curious on what the heck is going on really...

:popcorn:

I've replaced my actual host name with just "hostname" for privacy purposes:

```
May  3 11:03:32 hostname kernel: [1119807.136302] gdl_indexer[29799] general protection ip:7f352a5abeac sp:7f3529be7bf0 error:0 in libc-2.10.1.so[7f352a575000+166000]
May  3 11:08:34 hostname kernel: [1120109.275479] gdl_indexer[30283] general protection ip:7f28e9d9beac sp:7f28e93d7bf0 error:0 in libc-2.10.1.so[7f28e9d65000+166000]
May  3 11:10:36 hostname kernel: [1120231.489585] gdl_indexer[30652]: segfault at d ip 00007f8df0398805 sp 00007f8dedab9ef0 error 4 in ld-2.10.1.so[7f8df038d000+1f000]
May  3 11:11:39 hostname kernel: [1120293.713115] gdl_indexer[31237]: segfault at d ip 00007fb33aae3805 sp 00007fb338204ef0 error 4 in ld-2.10.1.so[7fb33aad8000+1f000]
May  3 11:12:41 hostname kernel: [1120355.708701] gdl_indexer[31543]: segfault at d ip 00007fd11ca2f805 sp 00007fd11a150ef0 error 4 in ld-2.10.1.so[7fd11ca24000+1f000]
May  3 11:13:43 hostname kernel: [1120417.657528] gdl_indexer[31714] general protection ip:7f6bbbe4fc68 sp:7f6bb9569fe0 error:0 in ld-2.10.1.so[7f6bbbe3d000+1f000]
May  3 11:15:45 hostname kernel: [1120539.675383] gdl_indexer[31903]: segfault at d ip 00007f4d30e11805 sp 00007f4d2e532ef0 error 4 in ld-2.10.1.so[7f4d30e06000+1f000]
May  3 11:17:49 hostname kernel: [1120663.858677] gdl_indexer[14696] general protection ip:7f322783feac sp:7f3226e7bbf0 error:0 in libc-2.10.1.so[7f3227809000+166000]
May  3 11:19:53 hostname kernel: [1120787.903088] gdl_indexer[15154]: segfault at d ip 00007fea9b755805 sp 00007fea98e76ef0 error 4 in ld-2.10.1.so[7fea9b74a000+1f000]
May  3 11:20:55 hostname kernel: [1120849.993674] gdl_indexer[15427] general protection ip:7f95a9cd4eac sp:7f95a9310bf0 error:0 in libc-2.10.1.so[7f95a9c9e000+166000]
May  3 11:22:59 hostname kernel: [1120974.094980] gdl_indexer[16126] general protection ip:7fb502e65eac sp:7fb5024a1bf0 error:0 in libc-2.10.1.so[7fb502e2f000+166000]
May  3 11:24:01 hostname kernel: [1121036.130960] gdl_indexer[16357] general protection ip:7fd9aa54feac sp:7fd9a9b8bbf0 error:0 in libc-2.10.1.so[7fd9aa519000+166000]
May  3 11:25:03 hostname kernel: [1121098.248264] gdl_indexer[16584] general protection ip:7f3ee942ac68 sp:7f3ee6b450a0 error:0 in ld-2.10.1.so[7f3ee9418000+1f000]
May  3 11:26:05 hostname kernel: [1121160.330847] gdl_indexer[17083] general protection ip:7f33292e0eac sp:7f332891cbf0 error:0 in libc-2.10.1.so[7f33292aa000+166000]
May  3 11:27:07 hostname kernel: [1121222.407729] gdl_indexer[17358] general protection ip:7fadc9966eac sp:7fadc8fa2bf0 error:0 in libc-2.10.1.so[7fadc9930000+166000]
May  3 11:28:09 hostname kernel: [1121284.461665] gdl_indexer[17619] general protection ip:7fe01db03eac sp:7fe01d13fbf0 error:0 in libc-2.10.1.so[7fe01dacd000+166000]
May  3 11:30:14 hostname kernel: [1121408.625349] gdl_indexer[18125] general protection ip:7fa71e06beac sp:7fa71d6a7bf0 error:0 in libc-2.10.1.so[7fa71e035000+166000]
May  3 11:31:16 hostname kernel: [1121470.685093] gdl_indexer[18622] general protection ip:7f5b47850eac sp:7f5b46e8cbf0 error:0 in libc-2.10.1.so[7f5b4781a000+166000]
May  3 11:33:20 hostname kernel: [1121594.787799] gdl_indexer[19166]: segfault at d ip 00007fd088642805 sp 00007fd085d63ef0 error 4 in ld-2.10.1.so[7fd088637000+1f000]
May  3 11:34:22 hostname kernel: [1121656.837552] gdl_indexer[19554] general protection ip:7fec3e36feac sp:7fec3d9abbf0 error:0 in libc-2.10.1.so[7fec3e339000+166000]
May  3 11:35:28 hostname kernel: [1121723.239991] gdl_indexer[20127] general protection ip:7f9e463edeac sp:7f9e45a29bf0 error:0 in libc-2.10.1.so[7f9e463b7000+166000]
May  3 11:36:30 hostname kernel: [1121784.922033] gdl_indexer[20558] general protection ip:7f1bec638eac sp:7f1bebc74bf0 error:0 in libc-2.10.1.so[7f1bec602000+166000]
May  3 11:37:32 hostname kernel: [1121847.055456] gdl_indexer[20956] general protection ip:7f13ac5cdeac sp:7f13abc09bf0 error:0 in libc-2.10.1.so[7f13ac597000+166000]
May  3 11:38:34 hostname kernel: [1121909.053885] gdl_indexer[21185] general protection ip:7f6bd07f6eac sp:7f6bcfe32bf0 error:0 in libc-2.10.1.so[7f6bd07c0000+166000]
May  3 11:39:36 hostname kernel: [1121971.125390] gdl_indexer[21422] general protection ip:7fabd6736eac sp:7fabd5d72bf0 error:0 in libc-2.10.1.so[7fabd6700000+166000]
May  3 11:40:38 hostname kernel: [1122033.196473] gdl_indexer[21722] general protection ip:7f79a6ca1c68 sp:7f79a43bc0a0 error:0 in ld-2.10.1.so[7f79a6c8f000+1f000]
May  3 11:41:40 hostname kernel: [1122095.252161] gdl_indexer[22200] general protection ip:7ff6c2078eac sp:7ff6c16b4bf0 error:0 in libc-2.10.1.so[7ff6c2042000+166000]
May  3 11:42:42 hostname kernel: [1122157.290554] gdl_indexer[22431]: segfault at d ip 00007fd8b39f7805 sp 00007fd8b1118ef0 error 4 in ld-2.10.1.so[7fd8b39ec000+1f000]
May  3 11:44:46 hostname kernel: [1122281.469614] gdl_indexer[22910] general protection ip:7f8cfdb54eac sp:7f8cfd7bebf0 error:0 in libc-2.10.1.so[7f8cfdb1e000+166000]
May  3 11:46:50 hostname kernel: [1122405.546798] gdl_indexer[23656] general protection ip:7f43c2265eac sp:7f43c1ecfbf0 error:0 in libc-2.10.1.so[7f43c222f000+166000]
May  3 11:47:53 hostname kernel: [1122467.701775] gdl_indexer[23884] general protection ip:7f4f1b473eac sp:7f4f1b0ddbf0 error:0 in libc-2.10.1.so[7f4f1b43d000+166000]
May  3 11:48:55 hostname kernel: [1122529.755995] gdl_indexer[24115] general protection ip:7f32e118beac sp:7f32e0df5310 error:0 in libc-2.10.1.so[7f32e1155000+166000]
May  3 11:49:57 hostname kernel: [1122591.822953] gdl_indexer[24371] general protection ip:7f70faeb2eac sp:7f70fab1cbf0 error:0 in libc-2.10.1.so[7f70fae7c000+166000]
May  3 11:50:59 hostname kernel: [1122653.890423] gdl_indexer[24645] general protection ip:7f9e63284eac sp:7f9e62eee310 error:0 in libc-2.10.1.so[7f9e6324e000+166000]
May  3 11:52:01 hostname kernel: [1122715.947640] gdl_indexer[25114] general protection ip:7f3df1653eac sp:7f3df12bd310 error:0 in libc-2.10.1.so[7f3df161d000+166000]
May  3 11:54:05 hostname kernel: [1122840.044757] gdl_indexer[25575] general protection ip:7f3b6d0feeac sp:7f3b6cd68140 error:0 in libc-2.10.1.so[7f3b6d0c8000+166000]
May  3 11:55:07 hostname kernel: [1122902.088602] gdl_indexer[25834] general protection ip:7fa4a8923eac sp:7fa4a858d3d0 error:0 in libc-2.10.1.so[7fa4a88ed000+166000]
May  3 11:56:09 hostname kernel: [1122964.395616] gdl_indexer[26427] general protection ip:7fb133896eac sp:7fb133500bf0 error:0 in libc-2.10.1.so[7fb133860000+166000]
May  3 11:57:11 hostname kernel: [1123026.289476] gdl_indexer[26671] general protection ip:7fcf92ffdeac sp:7fcf92c67bf0 error:0 in libc-2.10.1.so[7fcf92fc7000+166000]
May  3 11:58:13 hostname kernel: [1123088.362727] gdl_indexer[26905] general protection ip:7fa2cf746eac sp:7fa2cf3b0310 error:0 in libc-2.10.1.so[7fa2cf710000+166000]
May  3 11:59:15 hostname kernel: [1123150.440622] gdl_indexer[27169] general protection ip:7fe61d8dceac sp:7fe61d546310 error:0 in libc-2.10.1.so[7fe61d8a6000+166000]
May  3 12:00:17 hostname kernel: [1123212.481853] gdl_indexer[27446] general protection ip:7fd0d5b06eac sp:7fd0d57703d0 error:0 in libc-2.10.1.so[7fd0d5ad0000+166000]
May  3 12:01:19 hostname kernel: [1123274.530340] gdl_indexer[28038] general protection ip:7f06aeb3ceac sp:7f06ae7a6bf0 error:0 in libc-2.10.1.so[7f06aeb06000+166000]
May  3 12:02:21 hostname kernel: [1123336.570322] gdl_indexer[28267] general protection ip:7fd95561eeac sp:7fd955288bf0 error:0 in libc-2.10.1.so[7fd9555e8000+166000]
May  3 12:03:24 hostname kernel: [1123398.617203] gdl_indexer[28504] general protection ip:7f0c70b48eac sp:7f0c707b2310 error:0 in libc-2.10.1.so[7f0c70b12000+166000]
May  3 12:04:26 hostname kernel: [1123460.694074] gdl_indexer[28734] general protection ip:7fa626239eac sp:7fa625ea3bf0 error:0 in libc-2.10.1.so[7fa626203000+166000]
May  3 12:06:30 hostname kernel: [1123584.807145] gdl_indexer[29609] general protection ip:7fa169c16eac sp:7fa1698803d0 error:0 in libc-2.10.1.so[7fa169be0000+166000]
May  3 12:07:32 hostname kernel: [1123646.913480] gdl_indexer[29834] general protection ip:7fa556231eac sp:7fa555e9bbf0 error:0 in libc-2.10.1.so[7fa5561fb000+166000]
May  3 12:08:34 hostname kernel: [1123708.969802] gdl_indexer[30070] general protection ip:7f8912a07eac sp:7f8912671bf0 error:0 in libc-2.10.1.so[7f89129d1000+166000]

```

---

### Post by hamilyon on 2010-06-06
I have these messages too and following symptoms: no usb auto-detection, no reaction to power commands such as shutdown os suspend.


```
[  553.256190] gdl_indexer[5693] general protection ip:7f5be8176c29 sp:1ff2e50 error:0 in ld-2.10.1.so[7f5be8168000+1f000]
[  615.371658] gdl_indexer[6076] general protection ip:7f27ae4d5c29 sp:1c4be50 error:0 in ld-2.10.1.so[7f27ae4c7000+1f000]
[  797.510132] gdl_indexer[6504] general protection ip:7f8fe430cc29 sp:b56e50 error:0 in ld-2.10.1.so[7f8fe42fe000+1f000]
[  860.156668] gdl_indexer[7585] general protection ip:7f2f894f7c29 sp:e0ce50 error:0 in ld-2.10.1.so[7f2f894e9000+1f000]

```

---

### Post by trinaryouroboros on 2010-06-06
> **hamilyon said:**
> I have these messages too and following symptoms: no usb auto-detection, no reaction to power commands such as shutdown os suspend.


```
[  553.256190] gdl_indexer[5693] general protection ip:7f5be8176c29 sp:1ff2e50 error:0 in ld-2.10.1.so[7f5be8168000+1f000]
[  615.371658] gdl_indexer[6076] general protection ip:7f27ae4d5c29 sp:1c4be50 error:0 in ld-2.10.1.so[7f27ae4c7000+1f000]
[  797.510132] gdl_indexer[6504] general protection ip:7f8fe430cc29 sp:b56e50 error:0 in ld-2.10.1.so[7f8fe42fe000+1f000]
[  860.156668] gdl_indexer[7585] general protection ip:7f2f894f7c29 sp:e0ce50 error:0 in ld-2.10.1.so[7f2f894e9000+1f000]

```


I'm going to take an educated guess that "ld-2.10.1.so" is the problem here just for you, but since I also have an issue with this library, as well as libc-2.10.1.so - I'm guessing we both should probably hit up the people who develop the C libs?

---

