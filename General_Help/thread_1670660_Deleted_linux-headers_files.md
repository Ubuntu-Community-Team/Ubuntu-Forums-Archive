---
title: "Deleted linux-headers files"
date: 2011-01-19
forum: General Help
---

### Post by DrDaveyAtoms on 2011-01-19
I made a stupid mistake while cleaning up my long list of older kernels still installed on my machine. I acidentally deleted the linux-headers-2.6.35-23 and linux-headers-2.6.35-24 files but not the image files :oops:. I am not longer able to boot into Ubuntu with X windows running and can use only commands. 

I thought I would try and reinstall the above files using Synaptic, however, it is no longer allowing me to install anything. Synaptic tries to delete flgrx every time I try to install something from the repositories. It is here that it runs into difficulties. Specifically, I get:

```
Removing fglrx ...
dpkg-divert: mismatch on package
   when removing `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by fglrx'
   found `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
  fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Can anyone out there help me?

---

### Post by lithopsian on 2011-01-19
Time for the command line.
```
sudo apt-get install --reinstall linux-headers...
```

You'll probably get an error, but you can work from there.  It may suggest ways to recover from the error.

---

### Post by DrDaveyAtoms on 2011-01-19
> **lithopsian said:**
> Time for the command line.
```
sudo apt-get install --reinstall linux-headers...
```You'll probably get an error, but you can work from there.  It may suggest ways to recover from the error.

Thanks for the response lithopsian.

I have tried your suggestion and the errors I get are just the same as given on the original post. The problem seems to be that dpkg tries to remove fglrx every time it is used but this is not possible.

---

### Post by pl@yer on 2011-01-19
I've been stuck in a situation like this before. I just edited the postrm script so it will end successful. 

find out the name of the postrm script.
```

ls -l /var/lib/dpkg/info|grep -i fglrx|grep postrm

```
Edit that file and comment out set -e so it wont exit on any error and add exit 0 to the last line so it exits successful no matter what.
```

#!/bin/sh
#set -e
body of script
exit 0

```

**EDIT: I just wanted to point out that dpkg-reconfigure --force *packagename* would probably have worked here.**

---

### Post by lithopsian on 2011-01-19
> **DrDaveyAtoms said:**
> 
I have tried your suggestion and the errors I get are just the same as given on the original post. The problem seems to be that dpkg tries to remove fglrx every time it is used but this is not possible.

touch ... :)

---

### Post by DrDaveyAtoms on 2011-01-19
> **pl@yer said:**
> I've been stuck in a situation like this before. I just edited the postrm script so it will end successful. 

find out the name of the postrm script.
```

ls -l /var/lib/dpkg/info|grep -i fglrx|grep postrm

```Edit that file and comment out set -e so it wont exit on any error and add exit 0 to the last line so it exits successful no matter what.
```

#!/bin/sh
#set -e
body of script
exit 0

```

Thanks for this advice. It did indeed work and I was able to reinstall the linux-headers-X.X.XX-X files which I had accidentally deleted. 

Thanks so much for your help.

---

### Post by Laysan_A on 2011-01-19
Don't forget to "solve" your thread Doc! ;)

---

