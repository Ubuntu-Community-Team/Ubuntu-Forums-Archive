---
title: "I have problem with GParted.."
date: 2010-05-11
forum: General Help
---

### Post by ne7work on 2010-05-11
Please someone help me.. [http://imagebin.org/96416](http://imagebin.org/96416) :(

---

### Post by stevanbt on 2010-05-11
Sorry, what's the problem?

Thanks, Steve.

---

### Post by muteXe on 2010-05-11
This is the least descriptive problem I've ever seen on this forum. And that's saying something.

---

### Post by ne7work on 2010-05-11
I can't resize my partition?

---

### Post by muteXe on 2010-05-11
Are you booting from the live CD?

---

### Post by howefield on 2010-05-11
Post a screenshot of GParted in here, your image link above doesn't seem to be loading.

Alt + Printscreen will take a shot of only the active window.

---

### Post by muteXe on 2010-05-11
Worked for me.  Didnt really show anything useful though.

---

### Post by ne7work on 2010-05-11
[http://imagebin.org/96418](http://imagebin.org/96418)
and now in windows 7 after chkdisk.. [http://imagebin.org/96420](http://imagebin.org/96420)

---

### Post by ankspo71 on 2010-05-11
It says you need to check your hard drive for errors while using windows. by usinf the command chkdsk /f . I recommend doing it a couple of times, and defragment your hard drive a couple of times too. 

I personally would recommend chkdsk /r (or chkdsk /x) for a complete check but you have a large hard drive and it could take several hours. If you have the time, this is the best way to do it.

---

### Post by Mark Phelps on 2010-05-11
If you're running Win7, you should NOT be using GParted to mess with the OS partition; you should be using the Win7 Disk Management utility instead.

Also, you can't run chkdsk on the OS partition while running Win7.  You need to use the option to schedule a chkdsk on reboot and let it run.  You can't run it from inside a command window.

---

