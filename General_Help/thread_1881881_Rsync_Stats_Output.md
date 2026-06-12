---
title: "Rsync Stats Output"
date: 2011-11-16
forum: General Help
---

### Post by chrislynch8 on 2011-11-16
Hi,

Would somehere be able to explain the the stats output from Rsync with the --stats option. Here is an Exmaple of the output. This is information below my backup server to remotely connecting to another server and pulling the information.

```
Number of files: 329716 -- Number of file in backup directory
Number of files transferred: 1273 -- Actual Number of files Backed up
Total file size: 27.37G bytes -- Total File Size of Directory
Total transferred file size: 3.56G bytes -- Total Transferred File Size ??? seems to be alot 
Literal data: 126.77M bytes -- ?????
Matched data: 3.44G bytes -- ????
File list size: 6.60M -- ??
File list generation time: 0.015 seconds -- ??
File list transfer time: 0.000 seconds -- ??
Total bytes sent: 2.05M 
Total bytes received: 38.60M -- Bytes Received during the backup ?? should this not match the 3.5G above?

sent 2.05M bytes  received 38.60M bytes  49.79K bytes/sec -- Actaul data transferred? and data rate ?
total size is 27.37G  speedup is 673.19 -- ??
```

I googled this and one site mentioned that the Total Bytes received (in my case) should be the Literal data + overhead but this cannot be the case going by my results?

Rgds
Chris

---

