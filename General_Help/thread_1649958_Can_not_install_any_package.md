---
title: "Can not install any package"
date: 2010-12-20
forum: General Help
---

### Post by Pollyanna1 on 2010-12-20
I was installing some program from Ubuntu software center, and suddelny downloading have stopped and does not go further, I tried to exit from that Ubuntu Software Center but I could not... I restart the computer, then I tried to install another program from USC, but it gave me an error with instruction to run sudo pdkg --configer -a or something like that.,, I did it and try again to install from USC and still can not be able to install or download any program any more. ... 
I attached a picture for the error when I try to download from USC it may help for your understanding... 


I appreciate your help ...

---

### Post by MooPi on 2010-12-20
When you tried ```
sudo dpkg --configure -a
```
What was the response to that command ?
Because you misspelled the command just now.

---

### Post by Pollyanna1 on 2010-12-21
I just copy the command as it was instructed to me .., and it partially fix the problem... but not all.. (before I run the command I was not even able to get the download, after I run the command I was able to download may be %1 and then I got that meessage I attached with the first post) ... So the command was right when I typed it .. but may be some spilling mistake when I post it) !!!!

---

### Post by karthick87 on 2010-12-21
Try,

```
sudo apt-get clean
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by Pollyanna1 on 2010-12-21
IT works ,,,  great job ... thanks,,, 


By the way ...  Where can I learn ubuntu command and troubleshooting ????

---

