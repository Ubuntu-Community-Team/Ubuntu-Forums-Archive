---
title: "How to locate my pendrive in netbook edition"
date: 2011-01-29
forum: General Help
---

### Post by robinsh123 on 2011-01-29
Recently I switched to Ubuntu 10.10 Netbook edition in my Acer Aspire One D260, But now it's a major problem that how to locate and use my pendrive in it ??

I am sure that my Sandisk 8GB pendrive is showing there in the system storage options but I am getting it hard to use the same and currently unable to copy or paste data through the pendrive.

Please help me ASAP !!

Thanks

---

### Post by TeoBigusGeekus on 2011-01-29
Doesn't it show in the places menu?

---

### Post by robinsh123 on 2011-01-29
> **TeoBigusGeekus said:**
> Doesn't it show in the places menu?
How to get the places menu in netbook edition ?? 
while I got the same in my desktop edition.

---

### Post by TeoBigusGeekus on 2011-01-29
Oh yes, netbook...
Can you navigate to your /media folder? It should be in there if it's mounted.

---

### Post by robinsh123 on 2011-01-29
> **TeoBigusGeekus said:**
> Oh yes, netbook...
Can you navigate to your /media folder? It should be in there if it's mounted.
That is also not showing in media folder !!

---

### Post by TeoBigusGeekus on 2011-01-29
Open a terminal and type
```
sudo fdisk -l
```
Post us the results.

---

### Post by robinsh123 on 2011-01-29
> **TeoBigusGeekus said:**
> Open a terminal and type
```
sudo fdisk -l
```
Post us the results.
[IMG]http://img443.imageshack.us/img443/711/screenshotyrz.png[/IMG]

this is the the result !!

---

### Post by TeoBigusGeekus on 2011-01-29
Brilliant! Your pen drive is there - it's sdb1.
What is the output of 
```
ls /media/
```
?

---

### Post by robinsh123 on 2011-01-29
> **TeoBigusGeekus said:**
> Brilliant! Your pen drive is there - it's sdb1.
What is the output of 
```
ls /media/
```
?
nothing !! 

and giving the feedback as below :
[B]
robinsh123@Robinsh-PC:~$ ls /media/
robinsh123@Robinsh-PC:~$[/B]

---

### Post by TeoBigusGeekus on 2011-01-29
Ok, we just need to mount it.
```
sudo mkdir /media/PENDRIVE
```
to create a directory to mount it on
and then
```
sudo mount /dev/sdb1 /media/PENDRIVE
```

---

### Post by robinsh123 on 2011-01-29
> **TeoBigusGeekus said:**
> Ok, we just need to mount it.
```
sudo mkdir /media/PENDRIVE
```
to create a directory to mount it on
and then
```
sudo mount /dev/sdb1 /media/PENDRIVE
```
[IMG]http://img412.imageshack.us/img412/5076/screenshot1oz.png[/IMG]

It is not making the directory !

---

### Post by TeoBigusGeekus on 2011-01-29
Post us a screenshot of what you get when you give
```
ls /media/
```

---

### Post by robinsh123 on 2011-01-29
Okay thanks buddy problem is now solved. Thank you very much.

---

### Post by TeoBigusGeekus on 2011-01-29
Glad to hear that; don't forget to mark the thread as solved.

---

### Post by robinsh123 on 2011-01-29
Can You please help me with some more problems :-
[Network sharing problem desktop to netbook 10.10]("http://ubuntuforums.org/showthread.php?t=1678086") 
and 			 			[How to use my ubuntu desktop as a web host on the internet]("http://ubuntuforums.org/showthread.php?t=1678071")

---

