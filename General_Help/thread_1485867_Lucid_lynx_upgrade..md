---
title: "Lucid lynx upgrade."
date: 2010-05-17
forum: General Help
---

### Post by hargrave on 2010-05-17
Hello, have just upgraded to 10.04. All was fine for a day or so then I started getting messages telling me that my hard disc was full.This appeared to be associated with trying to use F spot. I have un installed F spot, but still same message if I try to do any thing. Even Thunderbird is behaving in a strange manner.
Have checked with disc usage analyser, and it shows total file system usage as 65%. Looking at the 2 volumes they agree.
This machine is dual booted and I can make no sense of the partitions.
Any help appreciated.   John.

---

### Post by pbpersson on 2010-05-19
post the output from the following command:

```
df -h
```

---

### Post by sandyd on 2010-05-19
post the output of ```
df -h
```

---

### Post by hargrave on 2010-05-19
Hello, and thank you both for your replies.
I am afraid that due to lack of knowledge I have wasted your time.
The file partition was full and all it needed was some files deleted.
I used g parted in an attempt to increase the partition size, but failed miserably, it would only let me reduce one partition to make unallocated space, but not increase the size of the one I need to make larger.
The system is usable now, and Ubuntu gives my much pleasure.   Regards John.

---

