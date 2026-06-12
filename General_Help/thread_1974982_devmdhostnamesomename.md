---
title: "/dev/md/hostname:somename ???"
date: 2012-05-06
forum: General Help
---

### Post by masuch on 2012-05-06
Hi,

I have created software raid 0 arrays.
when I boot up NON-RAID system I have got:

once upon a time it is mapped like 
/dev/md/somename
and after further reboot/s it is like:
/dev/md/hostname:somename

what is the rules about it ?

---my /etc/mdadm/mdadm.conf is:
...
#HOMEHOST <system>
...
ARRAY /dev/md/raid0ocz metadata=1.2 UUID=152fb8b4:95265477:57e0dde8:91307b7b name=raid0ocz
ARRAY /dev/md/raid0ext41 metadata=1.2 UUID=8248abdc:c6cb1226:1f60ded4:3b5dbffa name=raid0ext41
...

--- my /etc/fstab:
...
# --- RAID 0 first try:
/dev/md/raid0ocz       /media/raid0ocz       ext4     rw,suid,dev,exec,auto,nouser,async,acl,user_xattr,nobootwait,errors=remount-ro,noatime,discard 0 0
/dev/md/raid0ext41     /media/raid0ext41     ext4     rw,suid,dev,exec,auto,nouser,async,acl,user_xattr,nobootwait,errors=remount-ro 0 0

# --- RAID 0 if previous failed try following:
/dev/md/PCEUBU1:raid0ocz       /media/raid0ocz       ext4     rw,suid,dev,exec,auto,nouser,async,acl,user_xattr,nobootwait,errors=remount-ro,noatime,discard 0 0
/dev/md/PCEUBU1:raid0ext41     /media/raid0ext41     ext4     rw,suid,dev,exec,auto,nouser,async,acl,user_xattr,nobootwait,errors=remount-ro 0 0
...

--- it is happening as well when I am in busybox and/or grub prompt.

Does have any influence on creating /dev/md/somename LABEL/s of the raid partitions (to make name like /dev/md/partition-label) ?
I am asking about this because I do not know where else to look how OS figured out the mapping like /dev/md/hostname:somename(partition label) ? I have found that only partitions LABEL contain hostname string.


thank you for explanation or hint to better understand.
kind regards,
Martin

---

### Post by mattheworiordan on 2012-10-25
I have this exact same problem, on a server on EC2.

Did you ever find a solution to this?

---

### Post by mattheworiordan on 2012-10-25
BTW. I've just found a solution I don't undersand, but it works.

After updating your mdadm file, possibly with something like:
[FONT="Courier New"]mdadm --detail --scan >> /etc/mdadm/mdadm.conf[/FONT]

Simply run the following command
[FONT="Courier New"]update-initramfs -u[/FONT]

Then reboot, and everything will work as expected.

---

### Post by masuch on 2012-10-28
> **mattheworiordan said:**
> BTW. I've just found a solution I don't undersand, but it works.

After updating your mdadm file, possibly with something like:
[FONT="Courier New"]mdadm --detail --scan >> /etc/mdadm/mdadm.conf[/FONT]

Simply run the following command
[FONT="Courier New"]update-initramfs -u[/FONT]

Then reboot, and everything will work as expected.

Hi,
I did not find a solution but I am using the same workaround as you mentioned. I run from crontab 4 times daily update-initramfs -u -k all 
But I do not understand it anyway and did not figured out why.
In /etc/fstab I am using label name with all my raid0 arrays instead of /dev/something.

---

