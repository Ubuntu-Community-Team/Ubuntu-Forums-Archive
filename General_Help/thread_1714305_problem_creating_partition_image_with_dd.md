---
title: "problem creating partition image with dd"
date: 2011-03-25
forum: General Help
---

### Post by Tex-Twil on 2011-03-25
Hello,
I want to create a image of a partition using dd. The partition is 80GB but only 15 GB are used. I booted from a live CD and run this command to backup 20 GB

```

dd if=/dev/sda1 of=/mnt/backup/OLD_HDD/sda1.img bs=1M  count=20480

```

The command finishes without problems but when I mount the image I'm cannot read the content :

```

# mount -o loop /mnt/backup/OLD_HDD/sda1.img /mnt/sda1/
# ll /mnt/sda1/
ls: cannot access /mnt/sda1/proc: Input/output error
ls: cannot access /mnt/sda1/usr: Input/output error
ls: cannot access /mnt/sda1/bin: Input/output error
ls: cannot access /mnt/sda1/var: Input/output error
ls: cannot access /mnt/sda1/dev: Input/output error
ls: cannot access /mnt/sda1/home: Input/output error
ls: cannot access /mnt/sda1/boot: Input/output error
ls: cannot access /mnt/sda1/srv: Input/output error
ls: cannot access /mnt/sda1/mnt: Input/output error
ls: cannot access /mnt/sda1/sys: Input/output error
ls: cannot access /mnt/sda1/extra: Input/output error
ls: cannot access /mnt/sda1/initrd: Input/output error
ls: cannot access /mnt/sda1/opt: Input/output error
total 76
drwxr-xr-x  23 root root   4096 2011-03-08 13:39 ./
drwxr-xr-x   4 root root     80 2011-03-25 09:43 ../
d?????????   ? ?    ?         ?                ? bin/
d?????????   ? ?    ?         ?                ? boot/
lrwxrwxrwx   1 root root     11 2008-09-18 13:48 cdrom -> media/cdrom/
d?????????   ? ?    ?         ?                ? dev/
drwxr-xr-x 169 root root  12288 2011-03-25 09:36 etc/
d?????????   ? ?    ?         ?                ? extra/
d?????????   ? ?    ?         ?                ? home/
d?????????   ? ?    ?         ?                ? initrd/
lrwxrwxrwx   1 root root     33 2008-09-18 13:54 initrd.img -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  18 root root  12288 2011-03-18 09:58 lib/
drwx------   2 root root  16384 2008-09-18 13:48 lost+found/
drwxrwxr-x  13 root users  4096 2011-03-25 09:35 media/
d?????????   ? ?    ?         ?                ? mnt/
d?????????   ? ?    ?         ?                ? opt/
d?????????   ? ?    ?         ?                ? proc/
drwxr-xr-x  31 root root   4096 2011-03-25 09:19 root/
drwxr-xr-x   2 root root   4096 2011-03-18 09:58 sbin/
d?????????   ? ?    ?         ?                ? srv/
d?????????   ? ?    ?         ?                ? sys/
drwxrwxrwt  19 root root  16384 2011-03-25 09:36 tmp/
d?????????   ? ?    ?         ?                ? usr/
d?????????   ? ?    ?         ?                ? var/
lrwxrwxrwx   1 root root     30 2008-09-18 13:54 vmlinuz -> boot/vmlinuz-2.6.24-19-generic


```

any ideas ? 

Thanks,
Tex

---

### Post by lloyd_b on 2011-03-26
One thing you need to consider - just because it's only using 15Gb of that partition does *not* mean that all the data is stored in the first 15 (or 20) Gb of the partition.  Try the "dd", creating a full 80Gb copy of the partition instead of just the first 20Gb, and see if that works better.

Lloyd B.

---

### Post by Tex-Twil on 2011-03-26
> **lloyd_b said:**
> One thing you need to consider - just because it's only using 15Gb of that partition does *not* mean that all the data is stored in the first 15 (or 20) Gb of the partition.  Try the "dd", creating a full 80Gb copy of the partition instead of just the first 20Gb, and see if that works better.

Lloyd B.
right, that was the reason. I made a copy of the entire partition and it worked.

Is there a way to somehow trip the image so that it contains only the data ? 

cheers,
tex

---

### Post by dcstar on 2011-03-26
> **Tex-Twil said:**
> 
Is there a way to somehow trip the image so that it contains only the data ? 


No, that is not partition copying, that is **file** copying.

---

### Post by Tex-Twil on 2011-03-26
> **dcstar said:**
> No, that is not partition copying, that is **file** copying.

ok. Partimage does it but I need the partition to be mountable.

thanks for your help.

solved.

---

