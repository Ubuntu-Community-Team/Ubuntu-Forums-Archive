---
title: "Chroot problem"
date: 2010-07-06
forum: General Help
---

### Post by wcy1323 on 2010-07-06
Hi All,

I installed ubuntu server 9.10 as a proxy server. It ran well until yesterday. When I connected to this server, no command can be executed, and an error came out as below:
[INDENT]bash: ./ls: No such file or directory[/INDENT]

After I rebooted the system, the system can not start with below error:

[INDENT]chroot: cannot execute /etc/apparmor/initramfs: No such file or directory
run-init: /sbin/init: No such file or directory
[    4.883281] Kernel panic - not syncing: Attempted to kill init![/INDENT]

I use a live cd to boot the server, after I mounted the partition and tried to chroot to it, I saw the same error&#65306;
   
[INDENT]chroot: cannot execute "/bin/bash": No such file or directory[/INDENT]




Dose anyone know this problem?


thanks

---

### Post by Sanjeevtrip on 2010-07-06
The system didnt shutdown properly
what file system you are using.

did you chroot the mounted partition?

---

### Post by wcy1323 on 2010-07-06
> **Sanjeevtrip said:**
> The system didnt shutdown properly
what file system you are using.

did you chroot the mounted partition?

I use ubuntu server 9.10 64bit with EXT4. 
Yes, I chroot to the mounted partition.

I also thought that this was a file system problem, so I ran fsck -a /dev/sda2 in live cd. the fsck program didn't report any problem.

When I was using the live CD, I can executed the command in mounted partition directly, like:
    /mnt/1/bin/ls


Thank you

---

### Post by Sanjeevtrip on 2010-07-06
so you have only one partion /dev/sda2

see that you mount all the partitions, as in fstab, when you created

then

```

chroot /mnt/1

```

---

