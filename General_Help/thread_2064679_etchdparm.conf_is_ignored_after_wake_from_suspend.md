---
title: "/etc/hdparm.conf is ignored after wake from suspend"
date: 2012-09-30
forum: General Help
---

### Post by Bazon on 2012-09-30
Hello,

I want to spin down my external USB drive /dev/sdc as fast as possible:
/etc/hdparm.conf:
```
...
/dev/sdc {
	spindown_time = 1
}
```
that works, although I get 
```
$ sudo hdparm -C /dev/sdc

/dev/sdc:
SG_IO: bad/missing sense data, sb[]:  f0 00 01 00 50 40 00 0a 00 00 00 00 00 1d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 drive state is:  unknown
```


**The problem is after a suspend (system, not disc) and resume again, /dev/sdc doesn't spin down automatically anymore**. :-(

Any ideas?

---

### Post by Bazon on 2012-09-30
OK, got it. In a terminal:
```
cd /etc/pm/sleep.d/
sudo touch 20-hdparm
sudo chmod +x 20-hdparm 
sudo gedit 20-hdparm 
```
and there:
```
#!/bin/bash
case "$1" in
	thaw|resume)
		hdparm -S 1 /dev/sdc
		;;

esac
```

---

