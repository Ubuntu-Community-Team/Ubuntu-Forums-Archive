---
title: "kjournald Causing alot of diskio at idle."
date: 2009-12-19
forum: General Help
---

### Post by markp1989 on 2009-12-19
Im am very fussy about noise with my pc, at night when my server is idle, i can hear the drive park/unpark.


i used iotop to monitor disk activity, and turns out that kjournald is waking up the drive to write a few kb of data to the drive.

how can i reduce the disk io?

i already have my logs stored in tmpfs (there backed up to the drive every few hours using rsync)  

any way to reduce kjournald writes to the disk?

thanks Markp1989

edit: are there any programs like iotop that  can log disk activity rather then showing just current info?

thanks again, mark.

---

