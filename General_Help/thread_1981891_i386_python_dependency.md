---
title: "i386 python dependency"
date: 2012-05-17
forum: General Help
---

### Post by JohnPta on 2012-05-17
I installed Striata 64bit.
I did exactly what was advised on this website:

[http://www.striata.com/community/customer-support/striata-reader-64-bit-deb.html](http://www.striata.com/community/customer-support/striata-reader-64-bit-deb.html)

Now Ubuntu gives me this message:

"Not all updates can be installed

Problems with some of the installed software.
Unofficial software packages not provided by Ubuntu"

When you click here on "Close"
This message pops up:
"Software index is broken"

How can I un-install Striata and specially the "i386 python dependency"
Because I am sure that the "i386 python dependency" messes up my Ubuntu.

---

### Post by kc1di on 2012-05-17
if you want to remove it completely you would do this 

```
sudo dpkg -P striata
```

---

### Post by JohnPta on 2012-05-17
> **kc1di said:**
> if you want to remove it completely you would do this 

```
sudo dpkg -P striata
```

I tried it but got this as reply:
dpkg: warning: there's no installed package matching striata

---

### Post by kc1di on 2012-05-17
Try it this way 

```
sudo dpkg -P striata-reader-2.13-1
```

---

### Post by JohnPta on 2012-05-18
I got the same answer again. 

dpkg: warning: there's no installed package matching striata-reader-2.13-1

---

### Post by kc1di on 2012-05-18
then according to the package manager it is not installed on your system.

---

### Post by kc1di on 2012-05-18
So preform the following commands in a terminal and your error message should go away.

```
sudo apt-get autoclean 
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get update 
```
again copy them one at a time.
Good Luck,

---

### Post by JohnPta on 2012-05-21
I had a simpler solution this weekend. I just reinstalled the package 12.04 while enjoying a good glas of South African red wine. 
But thanks for the help anyway.

---

### Post by charlesall on 2012-06-08
JohnPta, have you got striata working on 12.04 64-bit?

Thanks
Charles

---

