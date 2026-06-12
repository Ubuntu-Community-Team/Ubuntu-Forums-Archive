---
title: "USB disk clone with dd, but still not exact copy"
date: 2010-12-11
forum: General Help
---

### Post by ASundman on 2010-12-11
Hi!

I'm trying to clone a 2GB USB memory stick to another stick just like it (same size and brand). 

The src drive has three partitions, one fat, one ext2 and one encrypted (in that order). It also has an mbr. 

I create the clone using the following command:
dd if=/dev/xxx of=/dev/xxx bs=512k conv=noerror,notrunc

Once it's done the mbr, the ext2 and the encrypted partitions seem fine, but the fat one is slightly modified on the clone. Any ideas to what might be causing this would be greatly appreciated.

Here is a hex dump of the (broken) clones fat partition followed by a dump of the original partition. 

"Clone":
0000000 3ceb 6d90 646b 736f 7366 0000 0402 0001
0000010 0002 0002 f800 00bc 003e 0040 0000 0000
0000020 f000 0002 0000 9f29 3bff 2032 2020 2020
0000030 2020 2020 2020 4146 3154 2036 2020 1f0e
0000040 5bbe ac7c c022 0b74 b456 bb0e 0007 10cd
0000050 eb5e 32f0 cde4 cd16 eb19 54fe 6968 2073
0000060 7369 6e20 746f 6120 6220 6f6f 6174 6c62
0000070 2065 6964 6b73 202e 5020 656c 7361 2065
0000080 6e69 6573 7472 6120 6220 6f6f 6174 6c62
0000090 2065 6c66 706f 7970 6120 646e 0a0d 7270
00000a0 7365 2073 6e61 2079 656b 2079 6f74 7420
00000b0 7972 6120 6167 6e69 2e20 2e2e 0d20 000a
00000c0 0000 0000 0000 0000 0000 0000 0000 0000
*
00001f0 0000 0000 0000 0000 0000 0000 0000 aa55
0000200 fff8 ffff 0000 0000 0000 0000 0000 0000
0000210 0000 0000 0000 0000 0000 0000 0000 0000
*
0001000 0701 0702 0703 0704 0705 0706 0707 0708
0001010 0709 070a 070b 070c 070d 070e 070f 0710

Original:
0000000 3ceb 6d90 646b 736f 7366 0000 0402 0001
0000010 0002 0002 f800 00bc 003e 0040 0000 0000
0000020 f000 0002 0000 9f29 3bff 2032 2020 2020
0000030 2020 2020 2020 4146 3154 2036 2020 1f0e
0000040 5bbe ac7c c022 0b74 b456 bb0e 0007 10cd
0000050 eb5e 32f0 cde4 cd16 eb19 54fe 6968 2073
0000060 7369 6e20 746f 6120 6220 6f6f 6174 6c62
0000070 2065 6964 6b73 202e 5020 656c 7361 2065
0000080 6e69 6573 7472 6120 6220 6f6f 6174 6c62
0000090 2065 6c66 706f 7970 6120 646e 0a0d 7270
00000a0 7365 2073 6e61 2079 656b 2079 6f74 7420
00000b0 7972 6120 6167 6e69 2e20 2e2e 0d20 000a
00000c0 0000 0000 0000 0000 0000 0000 0000 0000
*
00001f0 0000 0000 0000 0000 0000 0000 0000 aa55
0000200 fff8 ffff 0000 ffff 0005 0006 0007 0008
0000210 0009 000a 000b 000c 000d 000e 000f 0010
0000220 0011 0012 0013 0014 0015 0016 0017 0018
0000230 0019 001a 001b 001c 001d 001e 001f 0020
0000240 0021 0022 0023 0024 0025 0026 0027 0028

---

### Post by C.S.Cameron on 2010-12-11
What has seemed to work for me is simply:


```
dd if=/dev/sdx of=/dev/sdy
```


Edit:
Almost forgot, welcome to the forums.

---

### Post by dcstar on 2010-12-12
> **C.S.Cameron said:**
> What has seemed to work for me is simply:


```
dd if=/dev/sdx of=/dev/sdy
```

And if you are copying from an unreliable source, use **ddrescue** instead of dd.

---

### Post by ASundman on 2010-12-12
> **dcstar said:**
> And if you are copying from an unreliable source, use **ddrescue** instead of dd.

Thank you for turning me on to ddrescue. It didn't solve my problem though; it's just the same as before.

I managed to get a second USB stick and tried using that as a source and voila: it work!

So I guess the USB stick was broken.

---

