---
title: "GLIBC not found"
date: 2012-03-09
forum: General Help
---

### Post by mashumafi on 2012-03-09
Okay so I have 3 linux machines. One is my virtual machine, one is remote shared hosting 'jailbroken' and the other is remote but I cannot root. I have successfully compiled programs on my virtual machine before and transfered them to my remote machines and they ran. Just basic hello world programs for testing purposes. Recently I have been trying to compile ffmpeg on my virtual machine and it runs on my virtual mahcine and the second remote machine (using the same binaries). When I try to put the binaraies on my shared hosting machine and it say the following 3 lines when I try running the binaries:
 
./ffmpeg: /lib64/libz.so.1: no version information available (required by ./ffmpeg)
./ffmpeg: /lib64/libc.so.6: version `GLIBC_2.6' not found (required by ./ffmpeg)
./ffmpeg: /lib64/libc.so.6: version `GLIBC_2.7' not found (required by ./ffmpeg)
 
My main concern is the lines mentioning GLIBC, I have looked around and found the glibc version can be obtained using "ldd --version command", here is the result from all 3 machines
 
virtual:
ldd (Ubuntu EGLIBC 2.13-20ubuntu5) 2.13
Copyright (C) 2011 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
 
shared host:
dd (GNU libc) 2.5
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
 
remote:
ldd (Ubuntu EGLIBC 2.11.1-0ubuntu7.8) 2.11.1
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.
 
My shared hosting provider will not let me do anything on their server, but I know there must be a way to run this program on my shared host. The only linux machine I can change anything on is my virtual machine. Right now when I compile ffmpeg on my virtual machine I use the following commands as a sudo user:
 
./configure --prefix=/path/to/put/binaries && make -s && make install
 
I am not that great at linux, as you can see this is my first post, so do not just tell me to use one command without explaining or giving me a link as to why.
 
If I did not give enough info let me know. I have been trying to solve this problem for days, so any ideas are welcome.
 
Thanks.
Matt

---

### Post by Paddy Landau on 2012-03-10
May I ask why you are compiling ffmpeg? It should be installed by default with all Ubuntu (and family) distros.

Also, if not already done, install [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras").

---

