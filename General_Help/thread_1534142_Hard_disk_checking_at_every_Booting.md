---
title: "Hard disk checking at every Booting"
date: 2010-07-19
forum: General Help
---

### Post by srikrishnan on 2010-07-19
Hi All,

I have newly installed Ubuntu 10.04 lts. Everytime when I am boot my system, Ubuntu try to check my harddisk. I am stopping that by pressing "c" key.

Why it is so? anything problem with my hard disk or I need to disable anything for avoiding it for everytime?

Please help me

Thanks in Advance,
Srikrishnan

---

### Post by deathadder on 2010-07-19
Hi,

Have you let it run though? If you haven't it'll keep trying to check the drive, so it might be worth letting it check the drive once. What's on the drive it's trying to check? How old is the drive? Have you had any problems with it before?

You can disable it by changing the "<pass>" column in your /etc/fstab to 0. For example:
```

UUID=6a7a5ab5-1b57-4605-bbf1-df6770a0b398 / ext3    relatime,errors=remount-ro 0       1

```
Change to
```

UUID=6a7a5ab5-1b57-4605-bbf1-df6770a0b398 / ext3    relatime,errors=remount-ro 0       0

```
I wouldn't recommend simply changing it, as if fsck wants to check every time you boot there's probably a problem with the drive.

---

### Post by etdsbastar on 2010-07-19
> **srikrishnan said:**
> Hi All,

I have newly installed Ubuntu 10.04 lts. Everytime when I am boot my system, Ubuntu try to check my harddisk. I am stopping that by pressing "c" key.

Why it is so? anything problem with my hard disk or I need to disable anything for avoiding it for everytime?...

Please don't press the 'c' key, let fsck check the drive completely, and after your system starts please check your drive with the disk utility provided with native ubuntu install. its on system -> administration -> disk utility. Open it and select your drive and then check it using SMART Data button. 

Post the errors if any persists and also check if your disk is healthy (green light) is on.

Regards

---

