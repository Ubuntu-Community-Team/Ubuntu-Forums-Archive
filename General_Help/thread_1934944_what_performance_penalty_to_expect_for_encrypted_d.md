---
title: "what performance penalty to expect for encrypted devices?"
date: 2012-03-03
forum: General Help
---

### Post by akos.maroy on 2012-03-03
Hi,

I wonder what is a 'usual' performance penalty to be expected when using encrypted devices, like via luks.

I ran bonnie++ on an encrypted device and also on a non-encrypted one, same kind of HDD, and I see that the encrypted device is at least twice as slow - even though I'm using an intel i7 3.2GHz CPU.

the bonnie output for the encrypted devices is:

```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G  1037  90 47554   3 21067   1  3787  73 85261   3 105.5   1
Latency             11519us   21760ms   21809ms   84741us    3402ms    2041ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  4024   3 +++++ +++ 30207  20 15362  13 +++++ +++ 20631  14
Latency               338us     390us     463us     359us      58us     518us
1.96,1.96,rakku,1,1330766546,24G,,1037,90,47554,3,21067,1,3787,73,85261,3,105.5,1,16,,,,,4024,3,+++++,+++,30207,20,15362,13,+++++,+++,20631,14,11519us,21760ms,21809ms,84741us,3402ms,2041ms,338us,390us,463us,359us,58us,518us

```

while for the raw device:

```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G  1087  96 119751   7 54576   5  4955  94 154955   7 258.3   3
Latency             11024us     555ms     286ms   10635us   23583us    2021ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  6994   6 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency              9440us     389us     817us     407us      54us     656us
1.96,1.96,rakku,1,1330784343,24G,,1087,96,119751,7,54576,5,4955,94,154955,7,258.3,3,16,,,,,6994,6,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,11024us,555ms,286ms,10635us,23583us,2021ms,9440us,389us,817us,407us,54us,656us

```


is there an obvious way to improve encrypted device performance?

---

### Post by iponeverything on 2012-03-03
I use luks on two core2 laptops and and never notice that it is even there. 

It is worth it to me that if the hardware gets lifted at an airport or otherwise disappears, I won't have anything to worry about, as the data is much more valuable that the hardware.

---

### Post by Khayyam on 2012-03-03
Is this with a journaled filesystem on both the 'encrypted' and 'raw'? The former shouldn't be using a journal. Anyhow, its not likely to get noticably faster regardless, though choice of cypher, filesystem, etc, will all factor in.

best ... khay

---

### Post by akos.maroy on 2012-03-04
I made some comparative measurements yesterday, with the following scenarios:

[LIST]
[*]raw ext4 filesystem
[*]ext4 filesystem in an lvm volume
[*]encrypted device of a raw partition, ext4 on top
[*]lvm volume on an encrypted device, ext4 on the lvm volume
[*]encrypted device of an lvm volume, ext4 on top
[/LIST]

it seems there is a significant difference between encrypting an lvm volume, or creating an lvm volume on top of an encrypted device...

here are the measurements, in this order:

raw ext4 filesystem

```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G   753  95 78319   5 32202   3  3978  96 141259   7 124.4   1
Latency             10319us     621ms     423ms   22292us   85563us    2067ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 22559  19 +++++ +++ 13021   8 27286  21 +++++ +++ 28198  18
Latency               331us     370us     720us     347us      61us     489us
1.96,1.96,rakku,1,1330819247,24G,,753,95,78319,5,32202,3,3978,96,141259,7,124.4,1,16,,,,,22559,19,+++++,+++,13021,8,27286,21,+++++,+++,28198,18,10319us,621ms,423ms,22292us,85563us,2067ms,331us,370us,720us,347us,61us,489us

```

ext4 filesystem in an lvm volume

```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G   731  95 89299   5 33317   3  3326  87 139561   7 125.6   1
Latency             10917us     421ms     442ms   21914us   47740us    2078ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 22552  19 +++++ +++ 12388   8 24897  20 +++++ +++ 24903  16
Latency               335us     674us    4426us     344us     692us    2403us
1.96,1.96,rakku,1,1330821782,24G,,731,95,89299,5,33317,3,3326,87,139561,7,125.6,1,16,,,,,22552,19,+++++,+++,12388,8,24897,20,+++++,+++,24903,16,10917us,421ms,442ms,21914us,47740us,2078ms,335us,674us,4426us,344us,692us,2403us

```

encrypted device of a raw partition, ext4 on top

```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G   730  93 51649   3 28691   2  3430  86 138949   4 127.5   2
Latency             10777us   18793ms   18513ms   19953us   50133us   14121ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  5298   4 +++++ +++ 10940   7 +++++ +++ +++++ +++ 16453  10
Latency               367us     396us     520us     360us      60us     464us
1.96,1.96,rakku,1,1330823125,24G,,730,93,51649,3,28691,2,3430,86,138949,4,127.5,2,16,,,,,5298,4,+++++,+++,10940,7,+++++,+++,+++++,+++,16453,10,10777us,18793ms,18513ms,19953us,50133us,14121ms,367us,396us,520us,360us,60us,464us

```

lvm volume on an encrypted device, ext4 on the lvm volume


```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G   748  96 87708   6 44789   4  3805  96 139818   4 275.9   4
Latency             10813us    8273ms    8210ms    9638us   44491us     245ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 25930  22 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               346us     365us     474us     365us     582us     469us
1.96,1.96,rakku,1,1330815156,24G,,748,96,87708,6,44789,4,3805,96,139818,4,275.9,4,16,,,,,25930,22,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,10813us,8273ms,8210ms,9638us,44491us,245ms,346us,365us,474us,365us,582us,469us

```


encrypted device of an lvm volume, ext4 on top


```

Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
rakku           24G   743  94 55706   3 27685   2  3535  87 137570   4 120.5   2
Latency             11095us   16116ms   19422ms   13225us   51091us    2090ms
Version  1.96       ------Sequential Create------ --------Random Create--------
rakku               -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 26281  23 +++++ +++  9637   6 20598  18 +++++ +++ 30287  20
Latency               327us     348us     476us     347us      61us     530us
1.96,1.96,rakku,1,1330816207,24G,,743,94,55706,3,27685,2,3535,87,137570,4,120.5,2,16,,,,,26281,23,+++++,+++,9637,6,20598,18,+++++,+++,30287,20,11095us,16116ms,19422ms,13225us,51091us,2090ms,327us,348us,476us,347us,61us,530us

```

---

