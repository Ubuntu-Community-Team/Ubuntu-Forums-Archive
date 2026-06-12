---
title: "Enabling /dev/tcp"
date: 2009-08-30
forum: General Help
---

### Post by falconindy on 2009-08-30
I've found an infinite number of webpages and forum threads clearly stating that Debian and Ubuntu distros provide Bash compiled with --disable-net-redirections which disallows redirection to /dev/tcp and /dev/udp. On the other hand, I've found an incredibly **small** amount of information about how to "fix" this beyond "go recompile Bash". A thread on launchpad notes that Karmic comes with a version of bash which enables redirections. I'm currently running Jaunty, and upgrading isn't really feasible.

So, I've recompiled Bash (version 4.0.0)with --enable-net-redirections.  After searching around way too long, I finally came across the major and minor device IDs for the tcp and udp devices and created them with mknod. Essentially, this is my command history:
```
cd <bash source directory>
sudo su
./configure --enable-net-redirections
make
make install
mknod /dev/tcp c 30 36
mknod /dev/udp c 30 39
```However... I'm still unable to use these devices as redirection. I get results like:
```
[dave@panic:/] $ cat < /dev/tcp/time.nist.gov/13
bash: /dev/tcp/time.nist.gov/13: Not a directory
```Anyone know what I've missed?

---

### Post by falconindy on 2009-08-31
FWIW, my major and minor device numbers came from the Documentation.txt file in the Ubuntu kernel source. I don't suspect them to be wrong, but it's possible. Is there any other initialization required when using mknod? Are there any flags that need to be set with chmod, for example, to obtain the behavior I'm looking for?

---

### Post by falconindy on 2009-09-02
Someone must know...

---

### Post by falconindy on 2009-09-06
Anyone?

---

### Post by zlu on 2009-09-30
locate bash
you should get /usr/local/bin/bash
strings /usr/local/bin/bash | grep tcp
you should get /dev/tcp/*/*

you don't need to mknod, so just remove them

one last thing, after installing bash4.0, make sure you are issuing the command from that shell.

just to be sure, /usr/local/bin/bash, then issue the command again.

---

### Post by falconindy on 2009-10-19
> **zlu said:**
> locate bash
you should get **/usr/local/bin/bash**
strings /usr/local/bin/bash | grep tcp
you should get /dev/tcp/*/*

you don't need to mknod, so just remove them

one last thing, after installing bash4.0, make sure you are issuing the command from that shell.

just to be sure, /usr/local/bin/bash, then issue the command again.
That was the key. Even though I had recompiled and installed Bash 4, '/bin/bash --version' still returned 3.2.48. What threw me off is that 'bash --version' was somehow referencing /usr/local/bin instead of /bin. I moved /bin/bash aside and made a new symlink in its place pointing to /usr/local/bin/bash. All is well!

Thanks!

---

