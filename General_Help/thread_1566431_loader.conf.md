---
title: "loader.conf?????"
date: 2010-09-02
forum: General Help
---

### Post by bdemers on 2010-09-02
Trying to get driver installed, went to this manpage:

[http://manpages.ubuntu.com/manpages/hardy/man4/isp.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/isp.4.html)

The page tells me that one option is to load the driver during startup by inserting a line into loader.conf.  No such file exists, and wondering what file name should I be looking for.

Apparently loader.conf is for BSD and I wonder if any of this manpage is valid

---

### Post by quizno50 on 2010-09-02
What driver are you trying to install? I do believe that the Ubuntu hardware detection should auto detect these devices and install them for you. I'm sure these are compiled as modules. You might try:```
sudo modprobe isp
``` see what that does (I dunno much about this, never had to use it before). Also, what version of Ubuntu are you running?

---

### Post by bdemers on 2010-09-02
The link is for Hardy manpage.  Read it over.  You'll notice that according to this page the only way for me to get drivers for my qla2000 board is to custom the kernel, or, call a module at startup.  I want to try the module before tweaking the kernel.  This is where loader.conf comes into play.

---

### Post by quizno50 on 2010-09-02
ok.... First, in ubuntu the modules to load on startup is located in /etc/modules
After some googling, it looks like the module you want to insert is called qla2xxx. So try this:
```
modprobe qla2xxx
```
If that works for you, you can add qla2xxx to the /etc/modules file and it should load on boot.

---

### Post by bdemers on 2010-09-02
Love to be able to say that works, but modprobe comes up empty.

---

### Post by bdemers on 2010-09-02
Maybe I'm not using command correctly.  On this box I have a module lp which exists in the /etc/modules file.  Not rem'd out.  doing a modprobe lp doesn't return anything.  So, maybe I need to learn how to do that command befor I say that qla2xxx does't work

---

### Post by quizno50 on 2010-09-02
Since modprobe came up empty that usually means that the module inserted without any problems. You can try:
```
lsmod|grep qla2xxx
```
If that one comes up empty then something went wrong; if it spits out gla2xxx at you it should be fine and the driver is loaded.
You can check in /dev/ to see if your drives are there. Just try:
```
ls /dev/sd*
```
to see what's listed, then you can try mounting them to see if they're the drives your looking for.
**Edit**:
Another command that can be your friend when working with kernel modules is the dmesg command (might already know about it, but...). You can use:
```
dmesg|tail
```
to see the last few messages that the kernel has reported.

---

### Post by bdemers on 2010-09-02
You have something with the qla2xxx.  A search on this box (10.04) reveals qla2xxx in /lib/modules/ and /usr/src/ Now, what file will I use instead of loader.conf to put the line isp_load = "YES" ?

---

### Post by quizno50 on 2010-09-02
> Now, what file will I use instead of loader.conf to put the line isp_load = "YES" ?
I don't think you need that line. Just try putting the qla2xxx into your /etc/modules file, reboot and see what happens.

---

### Post by bdemers on 2010-09-02
doing lsmod returned valid info, so it appears that driver has in fact been loaded. 

Thanks.

---

