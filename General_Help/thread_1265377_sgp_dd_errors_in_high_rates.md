---
title: "sgp_dd errors in high rates"
date: 2009-09-13
forum: General Help
---

### Post by itai.agmon on 2009-09-13
Hi all,

I need to read data from SCSI device using FPDMA protocol in the highest rate possible. 
I have a disk that is full with X and I using a very simple bash script to read all the data from the disk. I use grep on the result and assert that there is no "0" character. 

From some weird reason, after a while, I start to get "0" characters instead of "X". This happens only when I use 16 threads and sector count of 2000 . 

I think that the spg_dd doe's not close all the threads.

This is the script I use:


```
#!/bin/bash

for ((i=0; i <=2000000; i+=2000 ));
do

       sgp_dd if=/dev/sg2 thr=16 count=2000 bs=512 skip=$i time=1 | grep 0

done
echo "Finished"

```I fully aware that this is a long shot, but doe's anyone have any idea what can cause such Phenomena ?

---

