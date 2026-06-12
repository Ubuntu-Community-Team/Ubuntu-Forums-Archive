---
title: "reallocate disk space"
date: 2010-06-02
forum: General Help
---

### Post by externalsupport on 2010-06-02
Hi all, 

on one of my servers I am almost down to 0% disk space on the /var partition

/dev/cciss/c0d0p1     897M  100M  750M  12% /
varrun                252M  424K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   68K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/cciss/c0d0p2     449M   18M  408M   5% /boot
/dev/cciss/c0d0p3     4.6G  464M  3.9G  11% /home
/dev/cciss/c0d0p5     897M  148M  702M  18% /tmp
/dev/cciss/c0d0p6     9.2G  432M  8.3G   5% /usr
/dev/cciss/c0d0p8      49G   47G  129M 100% /var

is it possible to reallocate some space from the /usr partition and assign it to the /var partition? How safe is it to do so?

Most of the space on /var is being used by svn and I don't want to risk breaking anything.

Thanks for your help

ste

---

### Post by xolot1 on 2010-06-02
Yes, I believe its possible, depending on how the partitions are formatted, although I cannot guarantee the safety of the operations. The two partitions must reside on the same disk, and be located next to one another, I think.

You'll want to use a partition editor to resize the partitions. I'd suggest the GParted Live CD found at [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php"). An example of how to resize a partition can be found here: [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

Again I can guarantee the success, but this would be my approach. 
Perhaps someone else can provide a second opinion.

---

