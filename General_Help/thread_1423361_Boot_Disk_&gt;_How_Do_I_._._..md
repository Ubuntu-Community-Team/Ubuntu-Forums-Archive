---
title: "Boot Disk &gt; How Do I . . ."
date: 2010-03-06
forum: General Help
---

### Post by YMS_1975 on 2010-03-06
I'm running Ubuntu 9.10 (Karmic Koala) on one of my PC's. I wish to format the drive so that the drive is 100% blank.

How do I accomplish this?

---

### Post by mohansathish on 2010-03-06
You tried System-> Administration-> Gparted??
That will help to format a drive you wish.

---

### Post by YMS_1975 on 2010-03-06
> **mohansathish said:**
> You tried System-> Administration-> Gparted??
That will help to format a drive you wish.

I tried that but I get an error message, and I think it's because the drive is currently in use by Ubuntu.

---

### Post by manoriax on 2010-03-06
Use a Live CD then.

---

### Post by YMS_1975 on 2010-03-06
> **manoriax said:**
> Use a Live CD then.

So if I put a Live CD in, there will be a format option, without installation? I just want the drive to be completely empty.

---

### Post by mohansathish on 2010-03-06
> **YMS_1975 said:**
> I tried that but I get an error message, and I think it's because the drive is currently in use by Ubuntu.
So are you trying to format the swap area? Or exactly where your ubuntu uses it?

---

### Post by manoriax on 2010-03-06
> **YMS_1975 said:**
> So if I put a Live CD in, there will be a format option, without installation? I just want the drive to be completely empty.
Boot the live system and go to system -> administration -> gparted. The very same way as on a normal Ubuntu system.

---

### Post by YMS_1975 on 2010-03-06
> **mohansathish said:**
> So are you trying to format the swap area? Or exactly where your ubuntu uses it?

I'm trying to format the entire drive so that it's completely clean of any information. I don't want anything on the drive whatsoever.

---

### Post by mohansathish on 2010-03-06
> **YMS_1975 said:**
> I'm trying to format the entire drive so that it's completely clean of any information. I don't want anything on the drive whatsoever.
To format the entire Hard Drive the solution is to use Live CD.
For a partition alone, Gparted helps

---

### Post by mk1w86 on 2010-03-06
If you want to wipe the entire drive take a look at DBAN:

[http://www.dban.org/](http://www.dban.org/)

---

### Post by YMS_1975 on 2010-03-06
> **mk1w86 said:**
> If you want to wipe the entire drive take a look at DBAN:

[http://www.dban.org/](http://www.dban.org/)

Thanks. Problem solved.  ;)

---

