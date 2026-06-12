---
title: "USB and firewire hfs+ drives now only read-only, need to move files, help"
date: 2009-09-16
forum: General Help
---

### Post by bjaz on 2009-09-16
hello all

i used to have no problems with my external hard drives, which are in HFS+ format.

all of a sudden they're all read only, and this is a big issue as I have 20 or so gigs on a hard drive that I need to transfer to an external HDD.

i've been looking it up, and trying things but so far nothing has worked

i'm on xubuntu jaunty, using gnome.

mount gives me 

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /media/a type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/<b type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

then

sudo fsck -r /dev/sdb1

gives me 

fsck 1.41.4 (27-Jan-2009)
fsck : fsck.hfsplus : not found
fsck : Erreur 2 while executing  fsck.hfsplus for /dev/sdb1



thanks in advance for your help

---

### Post by bjaz on 2009-09-16
i've tried this : 
but with no success
[http://www.debian-administration.org/users/lee/weblog/21](http://www.debian-administration.org/users/lee/weblog/21)

i also believe the disks were unplugged without dismounting, which could be the cause. but where's the solution ? now all external hfs+ disk mount as read only. i really need to fin a way to tranfer work files on to the mac i'm also using. can anyone help me fix this ?

thanks thanks thanks

b

---

### Post by bjaz on 2009-09-17
bump

can't anyone help out with this ? i really need to move data and i'm totally stuck.
please pretty please 

i really don't understand why all my removeable / external data storage is now read-only

thanks

ben

---

### Post by bjaz on 2009-09-26
I beg you, please can somebody help me solve this. please.

the only way out i can see is to reinstall the whole system

please, somebody please help me

thanks

ben

---

### Post by bjaz on 2009-10-03
bump

can someone please help ? I'm not going anywhere with discussions of similar subjects found online, and would really need to fix this. please.
I know no one is "entitled" to support, but not a single answer is a little rough
it's been weeks now

thanks in advance

---

### Post by CoolDreamZ on 2009-10-07
In your original post you used:

sudo fsck -r /dev/sdb1

However /dev/sdb1 is not listed as mounted in the output from mount! There appear to be 2 external drives:

/dev/sda5 on /media/a type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/<b type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

have you tried this:

sudo fsck -r /dev/sda5

or

sudo fsck -r /dev/sda2

---

### Post by bjaz on 2009-10-07
thanks

yes, I have quite a few NTFS+ external drive, but they all mount as read-only, even ones i'd never plugged in before, it's a generalized issue that I'm trying to fix.
before all the drives i used worked fine, read and write.

i'll try this

b

---

