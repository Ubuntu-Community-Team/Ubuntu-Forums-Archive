---
title: "I've got ext4_mb_generate_buddy errors on my ext4 partition"
date: 2011-10-24
forum: General Help
---

### Post by axishero on 2011-10-24
I use a old x86 to install ubuntu server with transmission to do downloads.Maybe a crash or unintentional shutdown cause these troubles:
```

mynas@ubuntu:~# dmesg
dy:736: group 7749, 0 blocks in bitmap, 534 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7751, 0 blocks in bitmap, 354 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7752, 0 blocks in bitmap, 22 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7754, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7755, 0 blocks in bitmap, 586 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7756, 0 blocks in bitmap, 661 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7757, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7758, 0 blocks in bitmap, 8 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7760, 0 blocks in bitmap, 117 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7766, 0 blocks in bitmap, 512 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7768, 0 blocks in bitmap, 52 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7772, 0 blocks in bitmap, 43 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7774, 0 blocks in bitmap, 30 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7776, 0 blocks in bitmap, 19 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7786, 0 blocks in bitmap, 93 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7788, 0 blocks in bitmap, 423 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7793, 0 blocks in bitmap, 278 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7797, 0 blocks in bitmap, 276 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7802, 0 blocks in bitmap, 512 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7806, 0 blocks in bitmap, 820 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7807, 0 blocks in bitmap, 360 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7937, 0 blocks in bitmap, 8 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7939, 0 blocks in bitmap, 303 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7941, 0 blocks in bitmap, 125 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7945, 0 blocks in bitmap, 348 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7956, 0 blocks in bitmap, 330 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7959, 0 blocks in bitmap, 1 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7961, 0 blocks in bitmap, 47 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7967, 0 blocks in bitmap, 27 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7971, 0 blocks in bitmap, 60 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7977, 0 blocks in bitmap, 76 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7979, 0 blocks in bitmap, 483 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7985, 0 blocks in bitmap, 51 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7987, 0 blocks in bitmap, 629 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7991, 0 blocks in bitmap, 212 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 7999, 0 blocks in bitmap, 26 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8005, 0 blocks in bitmap, 220 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8007, 0 blocks in bitmap, 245 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8009, 0 blocks in bitmap, 219 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8012, 0 blocks in bitmap, 3 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8016, 0 blocks in bitmap, 517 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8020, 0 blocks in bitmap, 139 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8022, 0 blocks in bitmap, 452 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8026, 0 blocks in bitmap, 146 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8038, 0 blocks in bitmap, 5 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8040, 0 blocks in bitmap, 155 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8042, 0 blocks in bitmap, 144 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8045, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8052, 0 blocks in bitmap, 66 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8058, 0 blocks in bitmap, 61 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8071, 0 blocks in bitmap, 290 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8079, 0 blocks in bitmap, 244 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8082, 0 blocks in bitmap, 434 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8085, 0 blocks in bitmap, 446 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8087, 0 blocks in bitmap, 38 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8091, 0 blocks in bitmap, 43 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8093, 0 blocks in bitmap, 448 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8095, 0 blocks in bitmap, 449 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8097, 0 blocks in bitmap, 5 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8099, 0 blocks in bitmap, 322 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8101, 0 blocks in bitmap, 559 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8118, 0 blocks in bitmap, 71 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8122, 0 blocks in bitmap, 128 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8124, 0 blocks in bitmap, 128 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8134, 0 blocks in bitmap, 12 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8146, 0 blocks in bitmap, 448 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8152, 0 blocks in bitmap, 416 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8158, 0 blocks in bitmap, 1 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8162, 0 blocks in bitmap, 92 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8166, 0 blocks in bitmap, 201 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8168, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8170, 0 blocks in bitmap, 2 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8184, 0 blocks in bitmap, 4 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8193, 0 blocks in bitmap, 6 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8200, 0 blocks in bitmap, 300 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8204, 0 blocks in bitmap, 63 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8210, 0 blocks in bitmap, 254 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8214, 0 blocks in bitmap, 462 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8216, 0 blocks in bitmap, 1 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8222, 0 blocks in bitmap, 291 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8224, 0 blocks in bitmap, 1 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8226, 0 blocks in bitmap, 459 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8228, 0 blocks in bitmap, 184 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8232, 0 blocks in bitmap, 63 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8244, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8246, 0 blocks in bitmap, 110 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8255, 0 blocks in bitmap, 429 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8265, 0 blocks in bitmap, 32 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8267, 0 blocks in bitmap, 4 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8273, 0 blocks in bitmap, 22 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8279, 0 blocks in bitmap, 44 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8281, 0 blocks in bitmap, 446 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8283, 0 blocks in bitmap, 469 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8291, 0 blocks in bitmap, 412 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8295, 0 blocks in bitmap, 216 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8297, 0 blocks in bitmap, 163 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8301, 0 blocks in bitmap, 385 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8448, 0 blocks in bitmap, 146 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8449, 0 blocks in bitmap, 630 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8450, 0 blocks in bitmap, 127 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8451, 0 blocks in bitmap, 167 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8452, 0 blocks in bitmap, 548 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8453, 0 blocks in bitmap, 1 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8455, 0 blocks in bitmap, 204 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8465, 0 blocks in bitmap, 80 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8477, 0 blocks in bitmap, 4 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8479, 0 blocks in bitmap, 412 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8481, 0 blocks in bitmap, 216 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8485, 0 blocks in bitmap, 31 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8489, 0 blocks in bitmap, 11 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8491, 0 blocks in bitmap, 250 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8493, 0 blocks in bitmap, 17 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8495, 0 blocks in bitmap, 299 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8501, 0 blocks in bitmap, 68 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8503, 0 blocks in bitmap, 242 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8505, 0 blocks in bitmap, 3 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8508, 0 blocks in bitmap, 506 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8513, 0 blocks in bitmap, 294 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8524, 0 blocks in bitmap, 136 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8547, 0 blocks in bitmap, 47 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8563, 0 blocks in bitmap, 311 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8569, 0 blocks in bitmap, 20 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8575, 0 blocks in bitmap, 67 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8579, 0 blocks in bitmap, 494 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8582, 0 blocks in bitmap, 22 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8586, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8590, 0 blocks in bitmap, 35 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8596, 0 blocks in bitmap, 506 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8599, 0 blocks in bitmap, 1 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8603, 0 blocks in bitmap, 26 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8605, 0 blocks in bitmap, 347 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8617, 0 blocks in bitmap, 19 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8621, 0 blocks in bitmap, 14 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8625, 0 blocks in bitmap, 268 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8626, 0 blocks in bitmap, 3 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8627, 0 blocks in bitmap, 58 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8628, 0 blocks in bitmap, 14 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8629, 0 blocks in bitmap, 135 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8631, 0 blocks in bitmap, 14 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8633, 0 blocks in bitmap, 55 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8634, 0 blocks in bitmap, 105 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8635, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8637, 0 blocks in bitmap, 470 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8641, 0 blocks in bitmap, 511 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8643, 0 blocks in bitmap, 405 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8646, 0 blocks in bitmap, 2 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8648, 0 blocks in bitmap, 45 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8651, 0 blocks in bitmap, 251 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8652, 0 blocks in bitmap, 19 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8655, 0 blocks in bitmap, 104 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8658, 0 blocks in bitmap, 32 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8664, 0 blocks in bitmap, 182 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8668, 0 blocks in bitmap, 128 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8672, 0 blocks in bitmap, 105 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8674, 0 blocks in bitmap, 97 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8678, 0 blocks in bitmap, 122 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8682, 0 blocks in bitmap, 13 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8686, 0 blocks in bitmap, 88 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8698, 0 blocks in bitmap, 282 in gd
EXT4-fs error (device sda2): ext4_mb_generate_buddy:736: group 8700, 0 blocks in bitmap, 75 in gd

```

I'd like to fix it without data loss.Because it's a 2TB drive full of data.I've googled a lot and got little useful information.Maybe in here someone can help.Thanks in advance.

---

### Post by axishero on 2011-10-25
Updated. I've run e2fsck -y.
dmesg still says:
EXT4-fs (sda2): error count: 1266
EXT4-fs (sda2): initial error at 1311783443: ext4_mb_generate_buddy:731
EXT4-fs (sda2): last error at 1319473021: ext4_mb_generate_buddy:736
Help in need!

---

