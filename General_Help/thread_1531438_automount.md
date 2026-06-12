---
title: "automount"
date: 2010-07-15
forum: General Help
---

### Post by ahso4271 on 2010-07-15
Hi
default 10.04 but never any CD gets mounted automatically. Do I need somehting etc?
Thanks

---

### Post by garvinrick4 on 2010-07-15
Look under drop down menu in Places.

Or in Panels add disk mounter to panels and you can mount and unmount from there also.

Make a couple 2 or 3 inches in panel for disk mounter. I like to use it myself.

---

### Post by cariboo on 2010-07-15
Udev looks after mounting cdroms, what is the output of:

```
dmesg | tail -n10
```

after you have inserted a CD?

---

### Post by ahso4271 on 2010-07-15
after a boot with a CD inside the tray:
chael@michael:~$ dmesg | tail -n10
[   14.281752] /dev/vmnet: open called by PID 1224 (vmnet-natd)
[   14.281759] /dev/vmnet: port on hub 8 successfully opened
[   14.328467] /dev/vmnet: open called by PID 1225 (vmnet-netifup)
[   14.328472] /dev/vmnet: port on hub 8 successfully opened
[   15.156505] /dev/vmmon[955]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445464883845242843 new 18445464883815979001 attempts 1
[   23.008005] eth0: no IPv6 routers present
[   24.192006] vmnet1: no IPv6 routers present
[   24.576010] vmnet8: no IPv6 routers present
[   28.809134] end_request: I/O error, dev fd0, sector 0
[   41.312743] end_request: I/O error, dev fd0, sector 0
michael@michael:~$ 

I also have some errors at boot alike: error reading /dev/sr0 
Thanks

---

### Post by ahso4271 on 2010-07-18
there was an entry in /etc/fstab for floppy. simply changed this to /dev/sr0 and cdrom

---

