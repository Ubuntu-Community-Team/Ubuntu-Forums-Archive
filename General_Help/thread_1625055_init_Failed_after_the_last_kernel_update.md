---
title: "init: Failed after the last kernel update"
date: 2010-11-18
forum: General Help
---

### Post by chek2fire on 2010-11-18
I just do the last kerne update to my ubuntu 10.10. When i done a reboot i stuck in ubuntu logo screen. If i press escape i see this error message

i> nit: Failed to spawn hostname main process: unable to execute: No such file or directory
init: Failed to spawn mountall post-stop process: unable to execute: No such file or directory

what i have to do to fix the problem and why this message?

---

### Post by chek2fire on 2010-11-19
anyone please?

---

### Post by chek2fire on 2010-11-20
I have find this solution

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1567147](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1567147)

and this commands

> 1. Boot liveCD
2. "sudo fdisk -l" to find your boot disk, in my case it is /dev/sda1.
3. "sudo mkdir /media/newroot"
4. "sudo mount /dev/sda1 /media/newroot", change sda1 to whatever your boot disk is.
5. "sudo chroot /media/newroot"

Now follow RufusVS's suggestion,

6. "ls /boot" to find your latest kenel. Mine has both 2.6.32-24-generic and 2.6.32-24-386. I don't know which one is causing the problem, so I updated both.
7. "sudo update-initramfs -u -k 2.6.32-24-generic"
8. reboot and smile.

but in step 5 chroot return this

chroot: cannot run command ' /bin/bash' : No such file or directory

i see that chroot have general problems

[http://www.computing.net/answers/linux/the-chroot-nightmare/4588.html](http://www.computing.net/answers/linux/the-chroot-nightmare/4588.html)

but i dont know what can i do to work chroot and finally fix my problem.

---

