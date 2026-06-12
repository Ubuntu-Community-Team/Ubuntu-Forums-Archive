---
title: "kernel module programming - problem with ioctl"
date: 2011-08-03
forum: General Help
---

### Post by KasiaT on 2011-08-03
Hey

It's my first post here so if I'll do something wrong please don't shout.

I have to write kernel module that communicate with DS1102 board. I was using kubuntu 10.04 and everything was ok. But since I have kubuntu 11.04 I can't compile my code. 
The problem is with ioctl function.

/home/kasia/DS1102modul/ds1102mod.c:68:1: error: unknown field ‘ioctl’ specified in initializer
/home/kasia/DS1102modul/ds1102mod.c:69:1: warning: initialization from incompatible pointer type

So the problem is with fops.
In my code it looks like: 

static struct file_operations fops = {
. read = device_read ,
. write = device_write ,
. open = device_open ,
. release = device_release,
. ioctl = device_ioctl
};

On kubuntu 10.04 it was working. I was trying to google it but I didn't find the answer.

And on 10.04 I included only #include <linux/ioctl.h> - it was enough. I thought that maybe when I include <sys/ioctl.h> it will solve my problem. But after including <sys/ioctl.h> I have information:
fatal error: sys/ioctl.h: No such file or directory

Do you have any idea what I should do?

---

### Post by KasiaT on 2011-08-03
OK. I found the answer.

It's here: 

[http://stackoverflow.com/questions/5868908/using-ioctl-communication-between-kernel-mode-and-user-mode](http://stackoverflow.com/questions/5868908/using-ioctl-communication-between-kernel-mode-and-user-mode)

---

### Post by Kira_Belka on 2011-08-03
mmmmm.. check where ioctl.h placed in ubuntu 11.04 .. if I remember you need to iclude it with follow code  <linux/ioctl.h>.. what mistakes it shows in this case?

---

