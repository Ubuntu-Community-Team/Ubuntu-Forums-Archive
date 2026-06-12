---
title: "how to make a shell script"
date: 2010-11-26
forum: General Help
---

### Post by arnavk007 on 2010-11-26
i want to make a shell script which copies 3 external drives and then puts the whole thing into the most compressable format and save it
also it should do so after every 24  hrs
how do i make such a script

---

### Post by nothingspecial on 2010-11-26
This will backup your external drive and give it a date

```
tar -cvf /where/you/want/to/save/it$(date +%y%m%d).tar /media/name/of/drive
```

You can use it with cron

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I suggest you have a look at rsync 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by arnavk007 on 2010-11-26
> **nothingspecial said:**
> This will backup your external drive and give it a date

```
tar -cvf /where/you/want/to/save/it$(date +%y%m%d).tar /media/name/of/drive
```

You can use it with cron

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I suggest you have a look at rsync 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
but the problem is this that the compression done by rsync is virtually useless
any alternative to make lzma or other format files from a drive

i want high compression ratio i dont care about access times and other stuff

---

### Post by arnavk007 on 2010-11-26
i want to have some thing like

```

cd /media/transfer
mkdir data

```
here i would like to do some way of making a txz archive or using xz as its compression ratios are very good
i wanna use the extreme option as the machine would be idle and would be on 24/7
also is there any way to do

---

### Post by asmoore82 on 2010-11-27
Keep in mind that all media formats (pictures, music and videos) are already compressed.

---

### Post by arnavk007 on 2010-11-27
what about isos

if thats the case then i have 1 question
does rsync function like cron i.e. can i give it a time at which it should copy the files

---

