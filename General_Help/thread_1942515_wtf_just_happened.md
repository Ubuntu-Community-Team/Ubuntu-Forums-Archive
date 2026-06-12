---
title: "wtf just happened"
date: 2012-03-17
forum: General Help
---

### Post by jha92 on 2012-03-17
I thought about trying out xubuntu 11.10 and i had a external hard drive with two partitions, one sized 10 gb and one about 300 gb. So i started copying the live image to the 10 gb partition by selecting the 10 gb partition and clicking "ERASE DISK". After that the program froze and gave some error wich i didn't read because I was panicking (Stupid me) and after that the 10 gb partition doesnt show up at all and the 300 gb partition wich previously had about 200gbs of music, pics and vids on it seems completely empty but gparted shows it has some data on it, could someone tell me what happened and can the data lost be rescued. Thank you in advance :) btw im running kubuntu 11.10

---

### Post by winh8r on 2012-03-17
First thing to do is stop using that disk immediately, if you want to have any chance of recovery.

Second, before you try and repartition or install anything it would be best to get what you can off that drive using testdisk/photorec

```
sudo apt-get install testdisk
```

you can find more info about testdisk/photorec here

[http://www.cgsecurity.org/]("http://www.cgsecurity.org/")

Read the wiki carefully before you attempt anything , and if you are unsure of how to proceed , please ask before you do anything!!

Hope this helps you

---

### Post by jha92 on 2012-03-18
TestDisk worked perfectly, all files recovered! Thank you so much ^^

---

### Post by winh8r on 2012-03-18
Glad it helped you.

Good Luck.

---

