---
title: "Need to make a file of an exact size for disk benchmarking?"
date: 2010-12-06
forum: General Help
---

### Post by TheOnlyMrK on 2010-12-06
Is their a command I could use to do this? It needs to be 32MB (33,554,432 bytes), can be either random data or just a blank file, though random data would be preferable, and well... that's it.

Though also, is their a way I could copy the file in a terminal and it print out the info such as average speed and/or total time it took to complete. I'm trying to fight some bad reviews on this flash drive I bought that performs very well, and since stupid comment vs stupid comment doesn't win anything I need to apparently be the first to actually test this drive throughly.

---

### Post by DaithiF on 2010-12-06
similar to this post: [http://ubuntuforums.org/showthread.php?p=10203171](http://ubuntuforums.org/showthread.php?p=10203171)

the solution there uses /dev/zero as input for the file-data, which fills the file with ascii-code 0 characters.  you could use /dev/random instead to fill the file with random data

for timing, just use the time shell keyword, e.g.:
```
time cp myfile destination

```

---

### Post by HermanAB on 2010-12-06
Here you go:
```
$ dd bs=1024 count=1000 if=/dev/urandom of=1megabyte
```

---

### Post by TheOnlyMrK on 2010-12-07
Thank you both of you ^^

---

### Post by HiImTye on 2010-12-07
flash drive performance is usually only limited by the system, not the drive. if it is usb 2.0 it's likely that it is being throttled by the packet size

---

