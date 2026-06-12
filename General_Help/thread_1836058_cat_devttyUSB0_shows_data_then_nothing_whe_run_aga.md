---
title: "cat /dev/ttyUSB0 shows data then nothing whe run again?"
date: 2011-08-30
forum: General Help
---

### Post by sdowney717 on 2011-08-30
confusing why is this?

> scott@scott-P5QC:~$ cat /dev/ttyUSB0
\$GPRMC,232042.000,V,3705.621,N,07618.743,W,0.0,0.0,280811,11.3,W*47
$GPGGA,232042.000,3705.62144,N,07618.74313,W,0,00,99.0,-00.76,M,-34.5,M,,*77
$GPVTG,0.0,T,348.7,M,0.0,N,0.0,K*46
$GPGSV,3,1,11,02,46,271,00,04,70,011,00,05,17,202,00,09,05,259,00*7D
$GPGSV,3,2,11,10,61,159,00,12,32,311,00,13,11,092,00,17,51,096,00*76
$GPGSV,3,3,11,20,06,039,00,23,11,066,00,28,09,162,00,,,,*40
$GPGSA,A,1,,,,,,,,,,,,,99.0,99.0,99.0*00
$GPRMC,232043.000,V,3705.621,N,07618.743,W,0.0,0.0,280811,11.3,W*46
$GPGGA,232043.000,3705.62144,N,07618.74313,W,0,00,99.0,-00.76,M,-34.5,M,,*76
$GPscott@scott-P5QC:~$ cat /dev/ttyUSB0
scott@scott-P5QC:~$ cat /dev/ttyUSB0
scott@scott-P5QC:~$ cat /dev/ttyUSB0
scott@scott-P5QC:~$ cat /dev/ttyUSB0
scott@scott-P5QC:~$ 


---

### Post by wt8008 on 2011-08-30
After you read all the data from ttyUSB0, the next time you read it there is no new data available *yet*.

---

