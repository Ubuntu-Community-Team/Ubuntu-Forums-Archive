---
title: "How to check disk for errors?"
date: 2012-03-14
forum: General Help
---

### Post by Shadius on 2012-03-14
My Ubuntu just freezes up and then sometimes goes into a command line-like screen with a bunch of lines. I have to restart my computer by holding my power button until it shuts down and then I restart it. As I'm typing this thread, it's freezing. What can be the problem? Is there a tool to check for bad sectors on my drive? Like in Windows how they have check disk? What should I do?

---

### Post by Rodney9 on 2012-03-14
```
sudo touch /forcefsck
```

should force a check on reboot

thanks to forestpiskie

---

### Post by winh8r on 2012-03-14
If your machine freezes , you should be able to do a restart by using this method:

Press and hold down the ALT key

Press and release the PrintScreen (PrtScr) key.

type these letters:

R E I S U B

This will avoid damaging the filesystem which can result by simply removing the power.

---

### Post by Shadius on 2012-03-14
> **Rodney9 said:**
> ```
sudo touch /forcefsck
```

should force a check on reboot

thanks to forestpiskie

Will this fix the errors also or do I have to type in another line of code?

---

### Post by Helen McCall on 2012-03-18
First check your logfiles for any errors.

If you are getting I/O errors on a disk these will show up in the syslog and probably in dmesg also.

---

