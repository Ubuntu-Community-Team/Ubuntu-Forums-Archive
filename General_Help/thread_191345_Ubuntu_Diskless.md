---
title: "Ubuntu Diskless"
date: 2006-06-07
forum: General Help
---

### Post by charafantah on 2006-06-07
hello...
i have a debian server that serves several systems to other terminals(diskless machines) on my network...

i decided to add Kubuntu 6.06, my problem lies that
each time i try to boot it from the network, it loads for a while, then pause after: 
*Loading device driver
with the error
```
nfs: RPC call returned error 101
```

after alot of experiments, i discovered that if i disable the service udev and  boot into runlevel 2...it will work and allow me to login...

offcourse the system is not usable like this, but at least i got to login :)

any ideas how to solve this?and why this is causing errors?

thanks,

ps: am trying to boot it with the same machine i originaly installed it on before moving it to the other server.. i.e. no hardware changes

---

### Post by charafantah on 2006-06-22
well, i think i solved that part...or at least a big part of it, it seems that udev had some problems, but now fixed and load fine.

my problem is that i can now boot into a shell(no X)...there are alot of errors complaining abuot /proc does not exist.

when i manually do:
```
mkdir /proc
mount -t proc /proc /proc
```

it works fine, until the next reboot, it freeze with the same error
```
nfs: RPC call returned error 101
```

then if you just rm -f /proc,,, it will work again

here is my fstab
```

#192.168.10.240:/raid/new_office_root   /               nfs     nfsvers=3,rw,bg,rsize=8192,wsize=8192 0 0
#192.168.10.240:/raid/ubuntu_root       /               nfs     nfsvers=3,rw,bg,rsize=8192,wsize=8192 0 0

proc            /proc           proc    defaults        0       0
/dev/nfs       /               nfs    defaults          1       1
none            /tmp            tmpfs   defaults        0       0
none            /var/run        tmpfs   defaults        0       0
none            /var/lock       tmpfs   defaults        0       0
none            /var/tmp        tmpfs   defaults,noexec,nosuid,nodev,size=50M        0       0
none            /media          tmpfs   defaults        0       0
none            /var/log        tmpfs   defaults        0       0
none            /var/lib/gdm    tmpfs   defaults        0       0

```

any ideas why is that happening?
how am i supposed to mount /proc  /sys  etc?shall i use init scripts or fstab is ok(i've seen some tutorials using fstab with no problems!!!)](*,)

---

### Post by charafantah on 2006-06-24
Thanks alot guys! you have been really helpful with ALL these answers :)

i finally sorted it out,, it was the networking script that caused all that(for some weird reason), i moved the network config to the kernel, and disabled this script, and now it loads just fine...(in case anyone got the same problem)

---

