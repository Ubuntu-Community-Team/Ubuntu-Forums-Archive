---
title: "Bootchart driving me NUTS!! /var/log/bootchart is always empty..."
date: 2010-07-14
forum: General Help
---

### Post by un234567 on 2010-07-14
I am trying to get bootchart to work on ubuntu lucid 64 bit.  I installed it from synaptic and reinstalled it about a 1000 times now but its not working. I searched a lot for solutions but no avail.

Here are the solutions i tried:

```
update-initramfs -u
update-initramfs -c -k "uname-r"

```
i checked if there is a script for update-initramfs in 

```
/usr/share/initramfs-tools/scripts/init-top/
```

it exists

then i went to check the runlevel using
```
sysv-rc-conf

```
bootchart had none of the runlevels selected, i checked 2,3,4,and 5 then rebooted but no use. I also tried to make it at the S runlevel. Btw i have open jdk java installed. Moreover, when I ran the command bootchart i got:


```
No path given, trying /var/log/bootchart.tgz
warning: path '/var/log/bootchart.tgz' does not exist, ignoring.
Parse error: empty state: '/var/log/bootchart.tgz' does not contain a valid bootchart
```

A final note, I am not using the generic kernel, I am using kernel 2.6.34 with the ureadahead patch, and ureadahead is working well. Also when bootchart was getting installed it mentioned something being added to ureadahead. Therefore I tried to install the generic kernel and run it but even with that the bootchart directory /var/log/bootchart stayed empty.

Im sorry for this long description but i am trying to make anyone who can help understand the problem well and i dont want people to be posting solutions which i tried. 
Any help is reaaaaaaaaaaaaaally appreciated

---

### Post by sohelmk on 2010-07-31
BUMP
exactly same issue on Ubuntu Lucid 10.3 on Dell Vostro

---

### Post by un234567 on 2010-09-11
BUMP
Im back from a long vacation and i still face this problem. My Ubuntu boot time increased significantly and I really wanna make bootchart work by any means possible...

Still fighting... any help is appreciated...

---

