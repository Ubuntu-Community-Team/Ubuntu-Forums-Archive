---
title: "need to remove tor!!!"
date: 2009-08-14
forum: General Help
---

### Post by stlsaint on 2009-08-14
so i was trying to install tor but i think i went wrong somewhere so know im trying to completely uninstall it...i didnt install from repos so i cant remove from there! i tried:
"sudo dpkg --purge tor"

and i got this:
stlsaint@stlsaint-laptop:~$ sudo dpkg --purge tor
[sudo] password for stlsaint: 
dpkg: dependency problems prevent removal of tor:
 tor-geoipdb depends on tor (>= 0.2.1.19-1~jaunty+1).
dpkg: error processing tor (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 tor
stlsaint@stlsaint-laptop:~$ 

any cmds out there to remove tor completely?!?!?

---

### Post by michy99 on 2009-08-14
Try this ```
sudo dpkg --purge tor-geoipdb tor
```

---

### Post by amvali on 2011-01-29
I tried "sudo dpkg --purge tor-geoipdb tor" and I got this:

ali@ali-desktop:~$ sudo dpkg --purge tor-geoipdb tor
[sudo] password for ali: 
dpkg: status database area is locked by another process
ali@ali-desktop:~$ 

Thanks,

---

