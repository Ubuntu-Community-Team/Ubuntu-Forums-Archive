---
title: "Mismatch between du and df"
date: 2010-07-22
forum: General Help
---

### Post by jtappin on 2010-07-22
I had some errors caused by /home being full, but when I checked, du and df give very different estimates of how much is on the disk (the numbers below are after removing a lot of thumbnail images).
```

james@xena:/home$ sudo df -h /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb9              11G  8.7G  1.8G  84% /home
james@xena:/home$ sudo du -hs /home
4.2G    /home
james@xena:/home$ 

```
The file system is ext3.
The Kubuntu version is Lucid.

Can anybody offer (a) an explanation and/or (b) a solution to the question of where the space has gone?

---

### Post by Sanjeevtrip on 2010-07-22
df shows disk space been allocated is being allocated
du shows the how much space the applications occupy
   every file has on average 2kB empty space which is ignored in du, 
   but shown in df.

also there should be some files removed while been read/written/processed, whose size appears in df, not in du.

---

### Post by jtappin on 2010-07-23
I don't think that cuts it. By doing
```

sudo find /home \( -type d -o -type f \) -ls > /scratch/james/home.csv

```
Then totalling the sizes and also the sizes rounded up to the next multiple of 4096, I get a less than 10% difference and both values are around the 4GB mark.

---

### Post by jtappin on 2010-07-25
A reboot fixed the mismatch, df now reports 4.3 Gb used.

No idea why!

---

### Post by gcbzzzz on 2010-07-25
wow. that should be a interesting but for you to submit.

if it ever happens again, submit `df -i` too, and `sudo lsof` (this may have personal data, it shows all open file names)

---

### Post by bakegoodz on 2010-07-25
Anybody know if a du ~, even touches all the hidden folders starting with "."
That might be it

---

### Post by jtappin on 2010-07-26
> **bakegoodz said:**
> Anybody know if a du ~, even touches all the hidden folders starting with "."
That might be it

I think it would. du -s * wouldn't. The find construction I used definitely showed them.

---

