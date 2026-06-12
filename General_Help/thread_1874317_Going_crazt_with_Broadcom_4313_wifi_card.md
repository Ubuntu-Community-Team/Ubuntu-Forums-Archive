---
title: "Going crazt with Broadcom 4313 wifi card"
date: 2011-11-02
forum: General Help
---

### Post by Learning0 on 2011-11-02
Hi there ,

how you doind ?

i hope you are all doing well

okay , i installed the latest version of backtrack which is bt5 r1
with the kernel 2.6.39.4 built on ubuntu

i completed now 24 hours of working hard just to enable the os 
to use wifi connection

only wired connection works

i tried to download the driver maunally from here :
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

but i couldn't install it , this error shows when i try to install :
```
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make: *** /lib/modules/2.6.39.4/build: No such file or directory.  Stop.
make: *** [all] Error 2
```then tryed to use this way :
System==>admin==>Hardware drivers

i found that broadcom driver is not activated
when i click on activate it gives me :
```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```and those are the last lines in the log file :
```
2011-11-03 03:27:48,637 WARNING: /sys/module/wl/drivers does not exist, cannot $
2011-11-03 03:27:48,645 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm4$
2011-11-03 03:27:53,178 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm4$
2011-11-03 03:27:53,284 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.con$
2011-11-03 03:27:53,387 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.con$
2011-11-03 03:27:53,399 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm4$
2011-11-03 03:27:53,411 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm4$
2011-11-03 03:27:53,518 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.con$
$rg.conf driver matches
```i tryed :
/etc/init.d/networking start
/etc/init.d/wicd start

still same problem , when i use wicd , it doesn't search for networks
just tells me no networks found

i found also a patch for wl , it didn't work also , gives me some error

please , can any one help me with this ?

i think the problem is with the kernel , how can i downgrade the kernel from
2.6.39.4 to 2.6.38 ?

:confused:
Thank you

---

### Post by Learning0 on 2011-11-04
up guys
 
any help ?

---

### Post by ka1z3r1 on 2011-11-21
I am having this exact same problem, glad to see it's not just me. I've tried everything and still can't get it to work.

---

