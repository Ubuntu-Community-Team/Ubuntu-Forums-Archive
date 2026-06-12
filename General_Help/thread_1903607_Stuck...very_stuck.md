---
title: "Stuck...very stuck"
date: 2012-01-02
forum: General Help
---

### Post by inurgentneed on 2012-01-02
Hi everyone
Thank you for taking the time to read this :)
Anyway I am really stuck
Earlier today I installed Ubuntu (love it btw) on my laptop
I tried to install it alongside W7, however I can't boot W7 at all now. I'm really scared it's gone forever. 
I don't have a working system restore disk and when I tried using start up manager to change the default operating system I couldn't find 7 there at all!
Please please help me?
Undying Gratitude,
Hugo

---

### Post by neu5eeCh on 2012-01-02
How sure are you that you didn't format the entire drive when you installed?

---

### Post by fdrake on 2012-01-02
can you post the output of the last command in the terminal (applications>accessories>termianl)
```

sudo apt-get install parted
sudo parted -l

```
just copy and paste here.

---

### Post by neu5eeCh on 2012-01-02
Hmm... Either it's not so urgent or his computer exploded.

What made you change fdisk -l to parted -l? Out of curiosity... Seemed like fdisk was a good place to start. I was wondering if he used 10.10 to resize his NTFS partition. I think that incarnation of pgarted had problems with NTFS.

---

### Post by fdrake on 2012-01-02
> **VTPoet said:**
> Hmm... Either it's not so urgent or his computer exploded.

What made you change fdisk -l to parted -l? Out of curiosity... Seemed like fdisk was a good place to start. I was wondering if he used 10.10 to resize his NTFS partition. I think that incarnation of pgarted had problems with NTFS.

well parted isn easier to read, (size and stuff like that), also it support/ recognizes formats that fdisk doesn't . example ntfs in fdisk is described as "HPFS/NTFS" (which one should I choose)? or ext3/4/2 are described all as "linux" with no distinction , well thanks a lot... :D


> Hmm... Either it's not so urgent or his computer exploded.LOL

---

