---
title: "Unable to mount UDF Volume"
date: 2010-01-23
forum: General Help
---

### Post by Pebble2009 on 2010-01-23
Hi Everyone.

I am trying to burn some data to CD/DVD, but when i insert a CD/DVD into the drive i get the 2 error messages shown in the screenshot below. The burn medium is not even recognised anymore by the PC.

This problem is new to me,it has suddenly appeared 3 days ago,and i have researched the forum already.

I have tried 5 other CD/DVD in the drive,but the problem is the same(some are brand new).

I&#7743; using Brasero/K3b programm to burn with,but alas no joy.

Anybody any ideas.

Thank you for reading

---

### Post by user1397 on 2010-01-23
> **Pebble2009 said:**
> Hi Everyone.

I am trying to burn some data to CD/DVD, but when i insert a CD/DVD into the drive i get the 2 error messages shown in the screenshot below. The burn medium is not even recognised anymore by the PC.

This problem is new to me,it has suddenly appeared 3 days ago,and i have researched the forum already.

I have tried 5 other CD/DVD in the drive,but the problem is the same(some are brand new).

I&#7743; using Brasero/K3b programm to burn with,but alas no joy.

Anybody any ideas.

Thank you for readingsome new blank cds and dvds come in the UDF format...can you try to format them to a different format in nautilus?

---

### Post by Pebble2009 on 2010-01-23
No i cant,because i cannot see any drive what i can click on to do a format,whether with nautilus or a burn programm.It simply doesnt show up

Ive just tried with some older dvds,where i know that there is data on,and they dont show up either.

Just the reoccuring error messages. 

A little frustrating,but as ever it will be something small and obvious that is causing it:D

thanks

---

### Post by Leppie on 2010-01-23
maybe a silly question, but have you tried installing the udf package:
```
sudo apt-get install libudf0
```

in my karmic install it wasn't installed by default

---

### Post by Pebble2009 on 2010-01-25
@Leppie.

No it wasnt installed,but it is now though :D.

It seems to have done the trick,i can see the CD/DVD in the drive now,and no more error messages.

Thankyou very much.

---

### Post by Leppie on 2010-01-25
> **Pebble2009 said:**
> @Leppie.

No it wasnt installed,but it is now though :D.

It seems to have done the trick,i can see the CD/DVD in the drive now,and no more error messages.

Thankyou very much.
you're welcome, glad it solved your issue :)

---

