---
title: "Systrace make error unknown type name"
date: 2011-11-13
forum: General Help
---

### Post by akshay.sulakhe on 2011-11-13
Hello friends, I am trying to install systrace for my project. I am running Ubuntu 11.04 32 bit edition. I downloaded the tarball,./configure goes fine,for the make command i am getting a error. Kindly let me know how to fix this error. Many thanks...

Make error while installing systrace is as follows :-

/Downloads/systrace-1.6g$ make
make all-recursive
make[1]: Entering directory `/home/akshay/Downloads/systrace-1.6g'
Making all in .
make[2]: Entering directory `/home/akshay/Downloads/systrace-1.6g'
gcc -DHAVE_CONFIG_H -I. -I. -I. -Wall -c systrace-translate.c
In file included from systrace-translate.c:54:0:
linux_fcntl.h:90:2: error: unknown type name ‘linux_off_t’
linux_fcntl.h:91:2: error: unknown type name ‘linux_off_t’
linux_fcntl.h:92:2: error: unknown type name ‘linux_pid_t’
linux_fcntl.h:98:9: error: unknown type name ‘linux_loff_t’
linux_fcntl.h:99:9: error: unknown type name ‘linux_loff_t’
linux_fcntl.h:100:9: error: unknown type name ‘linux_pid_t’
make[2]: *** [systrace-translate.o] Error 1
make[2]: Leaving directory `/home/akshay/Downloads/systrace-1.6g'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/akshay/Downloads/systrace-1.6g'
make: *** [all] Error 2

many thanks again... Have a good day...

---

### Post by mlkushan on 2012-08-07
Hello,

I am also having the same problem with Systrace. I am trying to install systrace-1.6f on Ubuntu 12.04 32bit edition. I am getting the following error.

gcc -DHAVE_CONFIG_H -I.     -Wall  -c systrace-translate.c
In file included from systrace-translate.c:54:0:
linux_fcntl.h:90:2: error: unknown type name ‘linux_off_t’
linux_fcntl.h:91:2: error: unknown type name ‘linux_off_t’
linux_fcntl.h:92:2: error: unknown type name ‘linux_pid_t’
linux_fcntl.h:98:9: error: unknown type name ‘linux_loff_t’
linux_fcntl.h:99:9: error: unknown type name ‘linux_loff_t’
linux_fcntl.h:100:9: error: unknown type name ‘linux_pid_t’

If anyone of you could suggest a solution, it would be highly appreciated.

Thanks in advance.
mlkushan

---

