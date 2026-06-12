---
title: "free disk space always zero!!"
date: 2010-07-19
forum: General Help
---

### Post by tux21 on 2010-07-19
I have a 6 month ubuntu 9.04 installation with custom kernel 2.6.30. Of lately i have noticed it shows Free space: 0 bytes in nautilus file browse. Whenever i try to copy something from other partition or save from web it shows disk full error. i have emptied trash, moved some 500 mb files to other partitions and also uninstalled packages but still 0 bytes.the "df -h && du -hx --max-depth=1" output are


4.0K	./selinux
6.1M	./bin
3.0G	./root
10G	./home
21M	./boot
0	./tmp
15M	./etc
148M	./lib
113K	./media
4.0K	./srv
8.4M	./sbin
326M	./opt
4.0K	./mnt
0	./dev
0	./proc
0	./sys
3.3G	./usr
227M	./var
16K	./lost+found
17G	.

/dev/sda5              19G   18G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  200K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  192K  1.5G   1% /dev
tmpfs                 1.5G   76K  1.5G   1% /dev/shm
overflow              1.0M  596K  428K  59% /tmp
/dev/sda1              47G   46G  1.1G  98% /media/VistaHP
/dev/sda6             108G  105G  2.9G  98% /media/HPtor
/dev/sda3              19G   16G  2.7G  86% /media/Vista64
/dev/sda2              19G   19G   22M 100% /media/ARCH
/dev/sdc8              35G   35G  761M  98% /media/WD30
/dev/sdc6              15G   15G  258M  99% /media/WDfedora
/dev/sdc3              14G   14G   22M 100% /media/WDmint
/dev/sdc7              12G   11G  1.3G  90% /media/WDTEMP
/dev/sdc1              63G   61G  1.7G  98% /media/WDxp
/dev/sdc2              11G  9.6G  772M  93% /media/WDslax


well then where is the empty space going? Thanks in advance because i won't do areinstall and my presentation is due.

---

### Post by tux21 on 2010-07-20
useless forum

---

### Post by mikewhatever on 2010-07-20
I think you need to investigate the /root - 3GB and /home - 10GB directories. Use du on them separately and post the output.

---

### Post by soltanis on 2010-07-20
> **tux21 said:**
> 
...
3.0G	./root
10G	./home

well then where is the empty space going? Thanks in advance because i won't do areinstall and my presentation is due.

I think you answered your own question, no?

---

### Post by drs305 on 2010-07-20
The 3GB in ./root is most likely undeleted 'root' trash. It isn't deleted when you empty your *own* trash. You can refer to this link on Disk Space to learn more about how to get rid of it.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")


There are other things to look for as well, detailed in the post.

---

### Post by tux21 on 2010-07-20
Thanks. baobab helped. i will read the link later. Also i suspect some free space is identified by gnome/ubuntu on reboots.

---

