---
title: "How to Disable USB Suspend?"
date: 2010-03-26
forum: General Help
---

### Post by matt11601 on 2010-03-26
My media server is running Ubuntu Server and has a 1TB USB drive connected. My problem is that Ubuntu will suspend/spin down the drive causing delays when accessing files. Also, the drive is accessed frequently so it's continually spinning down then back up all day. Is there any way to prevent this?

My search on Google and these forums weren't very helpful. The website I saw related to disabling this feature through the GUI but I'm using the server edition.

Can anyone offer some help?

Thanks.

-matt

---

### Post by cogier on 2010-03-26
Have you checked **System>Preferences>Power Management** setting has not got the "Spin down hard disk..." set?

---

### Post by matt11601 on 2010-03-26
I didn't install the GUI. Is there a way to do this from the command line?

---

### Post by cogier on 2010-03-26
Sorry that is beyond me.

---

### Post by Dmole on 2010-07-06
Try this
```
hdparm -S 0 /dev/sdi
```



p.s. you can use 
```
blkid
```
or
```
df -H
```
to get information about what drive to configure

---

### Post by matt11601 on 2010-07-07
Great. I'll give it a try.

---

