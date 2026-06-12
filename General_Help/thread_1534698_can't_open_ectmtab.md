---
title: "can't open /ect/mtab"
date: 2010-07-19
forum: General Help
---

### Post by savyboy24 on 2010-07-19
Hello,

On my Dell netbook. Hardy is installed. Something happened where I can connect to the internet but not get a page open. I thought it may be a hardware issue so I made a flash version to check it. When I try to mount the flash it says cant open /ect/mtab for writing. I have surfed tthe posts and every time I try something it tells me no such ect file. Not sure what is happening here any help would be great. This comp does not have a cd drive.

---

### Post by cariboo on 2010-07-19
You have a spelling error, it's **/etc/mtab**

How are you trying to mount your flash drive, it should automount when you plug it in.

---

### Post by savyboy24 on 2010-07-20
It tries to automount but says "cannot mount volume". "cant open /etc/mtab no such file or directory

---

### Post by savyboy24 on 2010-07-20
tried different spelling that didnt help

---

### Post by vikas.sood on 2010-07-20
/etc/mtab is a list of mounted volumes. you need privileges to mount. Seems like a permissions issue. try logging in with root and than plug in the drive.

---

### Post by savyboy24 on 2010-07-20
Got the flash to run and I can get internet with a live USB. So this is  not a hardware issue. I am connected to internet (I try wired and  wireless and get no ping return results). After some reading I found  people working on mtab and etc. I ran "ls -al /etc" it came back first  off ls cannot access /etc/mtab: Nosuch file or directory. The same came  up for /etc/resolv.conf

In the list where /etc/resolv.conf should be it says its name and then a  bunch of question marks.

Not sure if this is creating my internet problem. 

Any help is appreciated. Thanks

---

