---
title: "I can't boot in new kernel , after i updated it."
date: 2009-10-30
forum: General Help
---

### Post by netusernoname on 2009-10-30
hi everyone 

i upgraded my kernel from 2.6.28-16-generic to  kernel 2.6.31.5 amd after i upgraded it
i can not boot in new kernel i appear this error.

[B]Boot from (hd,0) ext3 2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
Error 15 : File not found
Press any key to continue

------------------------------------

and this my mount detail (when i (mount) in commandline)

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-16-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev

----------------------------------------

and this my menu.lst detail.
title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
kernel        /boot/memtest86+.bin
quiet

title           Ubuntu, kernel 2.6.31.5
uuid            2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea
kernel          /boot/vmlinuz-2.6.31-5 root=UUID=2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea ro quiet splash
initrd          /boot/initrd.img-2.6.31-5
quiet

----------------------------------------

what is my problem? and how i can fix it.

Many Thankyou


[/B]

---

### Post by LoloftheRings on 2009-10-30
Could you post the content of /boot? You could check it with a live cd.

---

### Post by falconindy on 2009-10-30
How did you upgrade your kernel?

Do the other kernels still boot?

Who/what added the entry in menu.lst?

"Boot from (hd,0) ext3 2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea"
The above looks suspicious -- it should be (hd0,0).

---

### Post by KegHead on 2009-10-30
Hi!

I'm also having huge problems with the kernel:

jim@jim-laptop:~$ ubuntu-bug linux
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 347, in <module>
    app = GTKUserInterface()
  File "/usr/share/apport/apport-gtk", line 35, in __init__
    apport.ui.UserInterface.__init__(self)
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 123, in __init__
    self.crashdb = get_crashdb(None)
  File "/usr/lib/python2.6/dist-packages/apport/crashdb.py", line 479, in get_crashdb
    execfile(conf, settings)
IOError: [Errno 2] No such file or directory: '/etc/apport/crashdb.conf'
jim@jim-laptop:~$ 

Any ideas?

KegHead

---

### Post by HardcoreSSG on 2009-10-30
I'm just going to let you know just incase. .31 doesn't run my intel graphics card. .28 does.
-------------------
Edit: .28 may run the graphics (**_very_** Laggy) But it does run them - I'm sure there's a solution somewhere, but even so you will not have sound. Again I'm sure there's a solution.

Are you running Karmic?

---

### Post by falconindy on 2009-10-30
> **KegHead said:**
> Hi!

I'm also having huge problems with the kernel:

jim@jim-laptop:~$ ubuntu-bug linux
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 347, in <module>
    app = GTKUserInterface()
  File "/usr/share/apport/apport-gtk", line 35, in __init__
    apport.ui.UserInterface.__init__(self)
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 123, in __init__
    self.crashdb = get_crashdb(None)
  File "/usr/lib/python2.6/dist-packages/apport/crashdb.py", line 479, in get_crashdb
    execfile(conf, settings)
IOError: [Errno 2] No such file or directory: '/etc/apport/crashdb.conf'
jim@jim-laptop:~$ 

Any ideas?

KegHead
Suggestion: start your own thread. That's a python error and has nothing to do with the kernel.

---

### Post by netusernoname on 2009-10-31
> **falconindy said:**
> How did you upgrade your kernel?
 
Do the other kernels still boot?
 
Who/what added the entry in menu.lst?
 
"Boot from (hd,0) ext3 2f2545f2-d1c7-4f5c-9e6d-a4563ed98dea"
The above looks suspicious -- it should be (hd0,0).
 
(hd,0)
That my wrong type . Sorry sir.

---

