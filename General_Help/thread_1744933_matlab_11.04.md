---
title: "matlab 11.04"
date: 2011-04-30
forum: General Help
---

### Post by a.w.baggaley on 2011-04-30
Hi all, I recently upgraded from 10.10 to 11.04 and have the following problems when opening and trying to produce anything in matlab which requires opengl:

/opt/matlab/bin/util/oscheck.sh: 619: /lib/libc.so.6: not found


any ideas?

---

### Post by yuval_harpaz on 2011-05-01
it seems to have been moved. I found it in /bin64/x86_64-linux-gnu. the target of this link is libc-2.13.so. make a new link like this:
sudo ln -s /lib64/x86_64-linux-gnu/libc-2.13.so /lib64/libc.so.6
hope it works

---

### Post by sukides on 2011-05-01
> **yuval_harpaz said:**
> it seems to have been moved. I found it in /bin64/x86_64-linux-gnu. the target of this link is libc-2.13.so. make a new link like this:
sudo ln -s /lib64/x86_64-linux-gnu/libc-2.13.so /lib64/libc.so.6
hope it works

Thanks, in 32bit Ubuntu 11.04 the libc.so.6 has been moved to /lib/i386-linux-gnu, making a soft link solve the problem.

---

### Post by martinianom on 2011-05-01
Had a similar problem, this fixed the problem. Thank you!

---

### Post by PenguinSHT on 2011-05-02
Thanks. I also solved my problem by making a soft link:

ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6

Steven

---

### Post by aliemim on 2011-05-05
> **PenguinSHT said:**
> Thanks. I also solved my problem by making a soft link:

ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6

Steven

Thanks. Worked for me too!

---

### Post by mlinuxy on 2011-06-02
thank you ,
it works for me 
iam i386 ,:D

---

### Post by huck22 on 2011-06-03
Since the error message tells you where the shell file is, you can simply update the directory for libc as follows:
Type in 
```
$ sudo su
$ gedit [Matlab directory]/bin/util/oscheck.sh
```
Replace line
```
ver=`/lib/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
```
with 
```
ver=`/lib/i386-linux-gnu/libc-2.13.so | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
```
and line
```
ver=`/lib64/libc.so.6 | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
```
with
```
ver=`/lib64/x86_64-linux-gnu/libc-2.13.so | head -n 1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`
```

---

