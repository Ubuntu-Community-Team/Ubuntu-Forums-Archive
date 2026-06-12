---
title: "How can I enable POSIX shared mem"
date: 2010-01-29
forum: General Help
---

### Post by Bryan55 on 2010-01-29
I found out from here that it is not enable.
 [http://How can I tell if POSIX shared memhttp://ubuntuforums.org/showthread.php?p=8739305#post8739305]("http://How%20can%20I%20tell%20if%20POSIX%20shared%20memhttp://ubuntuforums.org/showthread.php?p=8739305#post8739305")

I ran the command mount | grep "shm"
 and got.
none on /dev/shm type tmpfs (rw,nosuid,nodev)

So how do I enable it?
It is need for my ATI graphic card

Thanks for any help.


Ubuntu 9.10 64bit / Raid1 / Asus P7P55D MB / intel i5 / 4GB ram / Ati Radeon HD 4850

---

### Post by Bryan55 on 2010-01-29
I found the answer here

[http://ubuntuforums.org/showthread.php?t=122712](http://ubuntuforums.org/showthread.php?t=122712)

[I][I]To enable POSIX Shared Memory on your system, perform the following as root:

1. Add the following line to /etc/fstab (if it isn't there already): tmpfs /dev/shm tmpfs defaults 0 0
2. Mount shared memory as follows: mount /dev/shm
3. Issue the following command to check that it mounted properly: mount | grep "shm"

If the mount was successful, then the following output (or similar) should appear:
tmpfs on /dev/shm type tmpfs (rw)[/I][/I]

I can now have Visual Effects

Bryan

---

### Post by dirtyhabanero on 2010-08-20
who ever thought that using 'sudo' would make such a difference...thanks!

---

### Post by DjDiabolik on 2012-04-04
NOT WORKING ON UBUNTU 11.10!

I have add the line on fstab :
```
# POSIX SHARED MEMORY
tmpfs /dev/shm tmpfs defaults 0 0
```

And after that i manually mount with:
```
*[I]sudo mount /dev/shm*[/I]
```

But at the restart of ubuntu i don't see the tmpfs mounted!!!

This is the result of my terminal after restart:
```
diabolik@Diabolik-ubuntu:~$ mount | grep shm
none on /run/shm type tmpfs (rw,nosuid,nodev)
diabolik@Diabolik-ubuntu:~$ sudo gedit
[sudo] password for diabolik: 

```

---

