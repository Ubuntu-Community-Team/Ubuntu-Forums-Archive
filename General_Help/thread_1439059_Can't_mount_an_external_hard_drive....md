---
title: "Can't mount an external hard drive..."
date: 2010-03-25
forum: General Help
---

### Post by xhaansx on 2010-03-25
Hey!

I know there's a lot of threads out there regarding this issue, but I've tried a lot of them to no avail... Basically, I used to be able to mount my external hard drive ("Exodus" in the picture), but then after a day or two I started getting this error message. I can still mount the drive no problem on my vista boot.

Please help!!
-xhaansx

Error Message:
[http://yfrog.com/6xmountingerrormessagep](http://yfrog.com/6xmountingerrormessagep)

---

### Post by 666f6f on 2010-03-25
Can you open a terminal and run:
```
sudo mount /dev/sdf1 /media/sdf1
```

if that doesn't work try
```
sudo mount -t ntfs /dev/sdf1 /media/sdf1
```

What's the output of the above commands?

---

### Post by xhaansx on 2010-03-25
Sorry I lost the original output, but it said that the disk was "unclean" because it was "closed improperly on windows", and proceeded to fix it. It works again, like a charm! (First command that is, didn't use the second.)

Thank you!!

---

### Post by 666f6f on 2010-03-26
Super-cool!

---

