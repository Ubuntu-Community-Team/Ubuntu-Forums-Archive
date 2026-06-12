---
title: "how to use 7z"
date: 2011-02-28
forum: General Help
---

### Post by samir.raj on 2011-02-28
can anyone tell me how to extract files with the help of 7z??

---

### Post by Narchie on 2011-02-28
I installed 7Zip on my Ubuntu 10.10 machine, seems to integrate with archive manager (so you use archive manager as the GUI, there is no GUI for 7zip in linux from what I read).

---

### Post by samir.raj on 2011-02-28
yes . i am having trouble using command line

---

### Post by seawolf167 on 2011-02-28
Read up on the man file - it'll tell you the options to use that program

```
man 7z
```

make sure you have the full version too

```
sudo apt-get install p7zip-full
```

---

### Post by rolandrock on 2011-02-28
A simple example:

> paul@eeepc:~/demo$ ls -l
total 136
-rw-r--r-- 1 paul paul 136383 2011-03-01 01:39 filetobecompressed
paul@eeepc:~/demo$ 7z a compressedfile.7z filetobecompressed 

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_GB.utf8,Utf16=on,HugeFiles=on,1 CPU)
Scanning

Creating archive compressedfile.7z

Compressing  filetobecompressed      

Everything is Ok
paul@eeepc:~/demo$ ls -l
total 140
-rw-r--r-- 1 paul paul    691 2011-03-01 01:39 compressedfile.7z
-rw-r--r-- 1 paul paul 136383 2011-03-01 01:39 filetobecompressed
paul@eeepc:~/demo$ rm filetobecompressed 
paul@eeepc:~/demo$ ls -l
total 4
-rw-r--r-- 1 paul paul 691 2011-03-01 01:39 compressedfile.7z
paul@eeepc:~/demo$ 7z x compressedfile.7z 

7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_GB.utf8,Utf16=on,HugeFiles=on,1 CPU)

Processing archive: compressedfile.7z

Extracting  filetobecompressed

Everything is Ok

Size:       136383
Compressed: 691
paul@eeepc:~/demo$ ls -l
total 140
-rw-r--r-- 1 paul paul    691 2011-03-01 01:39 compressedfile.7z
-rw-r--r-- 1 paul paul 136383 2011-03-01 01:39 filetobecompressed
paul@eeepc:~/demo$ 

---

