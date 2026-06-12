---
title: "My book unmountable after accidental format"
date: 2009-07-11
forum: General Help
---

### Post by straferd on 2009-07-11
Hi everyone
 
I was using the USB Startup Disk Creatory, and unfocused as I was I managed to format the wrong disk. Instead of formating my 4 gig USB drive I formated my 1 TB My Book external HD....
 
The whole thing took less than a second, and now I can't mount it anymore in Ubuntu.
Windows recognize it, but want to format it. 
 
I started USB Startup Disk Creatory again, and it finds it under device /dev/sdc. And pity it says 1 TB free space (which was about 500 gig empty space before the format)... 
 
I really would like to recover the data. I have used foremost (sudo foremost -w -i /dev/sdc -o /recovery/foremost). however it ends with "Segmentation fault"
 
So any suggestions on how to recover the data and mount the drive would be appreciated.
 
Thanks.

---

### Post by prshah on 2009-07-11
> **straferd said:**
> 
So any suggestions on how to recover the data and mount the drive would be appreciated.

testdisk, failing that, photorec.

Both are in the repos, so they can be installed with a simple```
sudo apt-get install testdisk
```

testdisk will rebuild your entire drive, works excellently. 

photorec will recover your files (photos, docs, music, anything), but you will lose filenames. (All filenames will be replaced with a generic f0000000 type filename, but with a recognizable extension; eg such as mp3 for music, jpg for photos etc).

Post back if you find you cannot understand the testdisk interface (it requires some simple knowledge and understanding of HDD layout).

---

### Post by straferd on 2009-07-11
thanks for the tip, i will try that now

---

### Post by straferd on 2009-07-11
that didnt work. thats a pity tbh. 

thanks for the help tho.

---

