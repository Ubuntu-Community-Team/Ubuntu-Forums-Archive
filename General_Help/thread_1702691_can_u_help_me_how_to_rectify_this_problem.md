---
title: "can u help me how to rectify this problem"
date: 2011-03-08
forum: General Help
---

### Post by paidisetty on 2011-03-08
hi, i am having problem with this command. can u please help me in solving this problem.
ece90423@PMRAO:~/Downloads$ tar -xvfz '/home/ece90423/Downloads/mrtg.tar.gz' 
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by howefield on 2011-03-08
> **paidisetty said:**
> ece90423@PMRAO:~/Downloads$ tar -xvfz '/home/ece90423/Downloads/mrtg.tar.gz' 
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Try taking the quote marks out of the path, eg

```
tar -xvfz /home/ece90423/Downloads/mrtg.tar.gz
```


Or as it looks like you are already in the Downloads directory, try

```
ece90423@PMRAO:~/Downloads$ tar -xvfz mrtg.tar.gz
```

---

### Post by nothingspecial on 2011-03-08
> **paidisetty said:**
> hi, i am having problem with this command. can u please help me in solving this problem.
ece90423@PMRAO:~/Downloads$ tar -xvfz '/home/ece90423/Downloads/mrtg.tar.gz' 
tar: z: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

 mrtg.tar.gz is not in  /home/ece90423/Downloads/

You can just just click it and choose to extract

---

### Post by rnerwein on 2011-03-08
hi
try in your home: find . -name mrtg.tar.gz
if you find it --> cd in this directory and run: tar -xvfz mrtg.tar.gz
if you can't find it in your home "belongs on your browser configuration" 
---> cd / and run the find command again.
ciao

---

