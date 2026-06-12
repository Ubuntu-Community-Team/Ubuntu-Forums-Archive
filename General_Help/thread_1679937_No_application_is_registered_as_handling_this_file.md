---
title: "No application is registered as handling this file... DISC!"
date: 2011-02-01
forum: General Help
---

### Post by Zdeno.Pavlik on 2011-02-01
Hello geeks,
I have a problem with my Ubuntu (10.10). I have just installed software updates and now I cannot open disc partition named /media, it gaves me error **No applicatio is registered as handlins this file** and I dont know waht to do now. If you could help me, i will be pleased.. :-)
P.S. It cannot open only this one partition, other partitions works properly... :-)
Thanks.. :-)

---

### Post by tredegar on 2011-02-01
Maybe your file associations are messed up (It is a common problem, due to careless clicking).

R-Click on the directory that does not open.

Open with .... Other application

Select "File Browser".

Check "Remember...."

Problem should be fixed, if not please post more information.

---

### Post by Zdeno.Pavlik on 2011-02-01
no no no, I dont have problem with files.. I have problem with disc partition.. I had disc (/media), but after updates instalation I cannot open that partition (No application is registered as handling this file). And now, I dont see that disk in filesystem menu or anywhere else...

---

### Post by tredegar on 2011-02-02
OK
What is the output from

```
mount
sudo fdisk -l
cat /etc/fstab
```
?

---

