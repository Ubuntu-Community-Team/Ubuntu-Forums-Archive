---
title: "Ubuntu 11.10 uinput module"
date: 2012-04-06
forum: General Help
---

### Post by Geezanansa on 2012-04-06
Trying to use xboxdrv to get razer onza te working on oneric but i cannot load uinput 
```
lsmod | grep uinput
```does not show any error or anything else just prompt to new line


so..

```
sudo modprobe uinput
```    does not give any errors or anything else and then
```
lsmod | grep uinput 
```but nothing


How do i load uinput module so as to install/configure xboxdrv driver in ubuntu 11.10 64bit?

Thanks in advance.

---

### Post by potgietdl on 2012-04-07
Same question from my side (ubuntu 11.10), but for use with ps3 bd remote and bluetooth driver.

Thanks
Derick

---

### Post by qualtch on 2012-06-07
EDIT: Comment removed by author, the issue was in my code after all.

---

### Post by Geezanansa on 2012-09-20
```
sudo modprobe uinput
``` will load uinput module
```
sudo rmmod xpad
``` will remove xpad module
```
lsmod
``` will list loaded modules

It has taken a fair bit of time and effort to get xboxdrv running but is more than worth while.  Simple lack of understanding has been a hinderance but really rewarding project for learning a bit of command understanding layout of arguements etc and now xboxdrv is running am now looking at making launch script file so a bit of bash education undergoing.  Have found that the answer is all most certainly in all cases staring me in the face.

---

