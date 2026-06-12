---
title: "Mounting problem, find out the missing directory"
date: 2011-11-07
forum: General Help
---

### Post by yanij on 2011-11-07
Hi everyone,

Just earlier today I wanted to setup a FTP mount point on my server so I used CurlFtpFS and everything goes well.

But the problem is I accidentally set it to my local home directory and the FTP "seemed" to overwrite my whole directory. I immediately umount it and stop the CurlFtpFS from mounting but yet it's too late.

All I get now is 
drwxr-xr-x  8 root   root   4.0K 2011-05-23 17:19 ..
d?????????  ? ?       ?          ?                ? ME

and when i try to "ls" or get into my directory it shows

ls: cannot access ME: Transport endpoint is not connected


So what can I do now ?? please help... 

yanij

---

### Post by ajgreeny on 2011-11-07
You should be able to find your /home folder by using a live CD/USB to boot the server, but that requires the appropriate hardware, of course.  You should be able to use a CD that boots to a command line, if necessary, and then find your original /home.

You should also be able to re-edit the /etc/fstab file, or whatever was changed when using CurlFtpFS.

---

