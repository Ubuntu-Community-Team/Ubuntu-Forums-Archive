---
title: "Problem with package winbind"
date: 2010-10-11
forum: General Help
---

### Post by w33k on 2010-10-11
Hello,

for some reason the package winbind is misbehaving. A few upgrades ago I suddenly started getting this error message each time I try to upgrade or install winbind (or any other package). 

```
john@john-desktop:~$ sudo apt-get upgrade 
[sudo] password for johnny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up winbind (2:3.5.4~dfsg-1ubuntu8) ...
 * Starting the Winbind daemon winbind                                   [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Anyone has similar problems or can pose a solution?

- w33k

---

### Post by happyhamster on 2010-10-11
Try running:

```

sudo dpkg --configure -a
sudo apt-get -f install

```

If that doesn't work, could you show the output of the following command:
```

strace -f dpkg --configure winbind 2>&1 | grep execve

```
It should identify the post-installation script that is failing (and show its location). Good luck.

---

### Post by w33k on 2010-10-11
I've tried the dpkg --configure -a before to no avail but here's the output.

```
sudo dpkg --configure -a
Setting up winbind (2:3.5.4~dfsg-1ubuntu8) ...
 * Starting the Winbind daemon winbind                                   [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 winbind
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up winbind (2:3.5.4~dfsg-1ubuntu8) ...
 * Starting the Winbind daemon winbind                                   [fail] 
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Here's the output of 
strace -f dpkg --configure winbind 2>&1 | grep execve
```
sudo strace -f dpkg --configure winbind 2>&1 | grep execve
execve("/usr/bin/dpkg", ["dpkg", "--configure", "winbind"], [/* 16 vars */]) = 0
[pid  6480] execve("/var/lib/dpkg/info/winbind.postinst", ["/var/lib/dpkg/info/winbind.posti"..., "configure", ""], [/* 20 vars */] <unfinished ...>
[pid  6480] <... execve resumed> )      = 0
[pid  6481] execve("/usr/bin/getent", ["getent", "group", "winbindd_priv"], [/* 21 vars */]) = 0
[pid  6482] execve("/usr/bin/dpkg", ["dpkg", "--compare-versions", "", "lt-nl", "3.0.25b-2"], [/* 21 vars */]) = 0
[pid  6483] execve("/usr/sbin/pam-auth-update", ["pam-auth-update", "--package"], [/* 21 vars */]) = 0
[pid  6483] execve("/usr/share/debconf/frontend", ["/usr/share/debconf/frontend", "/usr/sbin/pam-auth-update", "--package"], [/* 22 vars */]) = 0
[pid  6484] execve("/usr/local/sbin/locale", ["locale", "charmap"], [/* 22 vars */]) = -1 ENOENT (No such file or directory)
[pid  6484] execve("/usr/local/bin/locale", ["locale", "charmap"], [/* 22 vars */]) = -1 ENOENT (No such file or directory)
[pid  6484] execve("/usr/sbin/locale", ["locale", "charmap"], [/* 22 vars */]) = -1 ENOENT (No such file or directory)
[pid  6484] execve("/usr/bin/locale", ["locale", "charmap"], [/* 22 vars */] <unfinished ...>
[pid  6484] <... execve resumed> )      = 0
[pid  6485] execve("/bin/sh", ["sh", "-c", "stty -a 2>/dev/null"], [/* 22 vars */]) = 0
[pid  6486] execve("/bin/stty", ["stty", "-a"], [/* 22 vars */]) = 0
[pid  6487] execve("/bin/sh", ["sh", "-c", "stty -a 2>/dev/null"], [/* 22 vars */] <unfinished ...>
[pid  6487] <... execve resumed> )      = 0
[pid  6488] execve("/bin/stty", ["stty", "-a"], [/* 22 vars */]) = 0
[pid  6489] execve("/usr/sbin/pam-auth-update", ["/usr/sbin/pam-auth-update", "--package"], [/* 23 vars */]) = 0
[pid  6490] execve("/usr/local/sbin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6490] <... execve resumed> )      = -1 ENOENT (No such file or directory)
[pid  6490] execve("/usr/local/bin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6490] <... execve resumed> )      = -1 ENOENT (No such file or directory)
[pid  6490] execve("/usr/sbin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6490] <... execve resumed> )      = -1 ENOENT (No such file or directory)
[pid  6490] execve("/usr/bin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6490] <... execve resumed> )      = 0
[pid  6491] execve("/usr/local/sbin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6491] <... execve resumed> )      = -1 ENOENT (No such file or directory)
[pid  6491] execve("/usr/local/bin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6491] <... execve resumed> )      = -1 ENOENT (No such file or directory)
[pid  6491] execve("/usr/sbin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6491] <... execve resumed> )      = -1 ENOENT (No such file or directory)
[pid  6491] execve("/usr/bin/md5sum", ["md5sum"], [/* 23 vars */] <unfinished ...>
[pid  6491] <... execve resumed> )      = 0
[pid  6492] execve("/usr/local/sbin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6492] execve("/usr/local/bin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6492] execve("/usr/sbin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6492] execve("/usr/bin/md5sum", ["md5sum"], [/* 23 vars */]) = 0
[pid  6493] execve("/usr/local/sbin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6493] execve("/usr/local/bin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6493] execve("/usr/sbin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6493] execve("/usr/bin/md5sum", ["md5sum"], [/* 23 vars */]) = 0
[pid  6494] execve("/usr/local/sbin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6494] execve("/usr/local/bin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6494] execve("/usr/sbin/md5sum", ["md5sum"], [/* 23 vars */]) = -1 ENOENT (No such file or directory)
[pid  6494] execve("/usr/bin/md5sum", ["md5sum"], [/* 23 vars */]) = 0
[pid  6495] execve("/usr/sbin/update-rc.d", ["update-rc.d", "winbind", "defaults"], [/* 21 vars */]) = 0
[pid  6496] execve("/usr/bin/which", ["which", "invoke-rc.d"], [/* 21 vars */]) = 0
[pid  6497] execve("/usr/sbin/invoke-rc.d", ["invoke-rc.d", "winbind", "start"], [/* 21 vars */]) = 0
[pid  6500] execve("/bin/sed", ["sed", "s/.*\\ //"], [/* 21 vars */]) = 0
[pid  6499] execve("/sbin/runlevel", ["/sbin/runlevel"], [/* 21 vars */] <unfinished ...>
[pid  6499] <... execve resumed> )      = 0
[pid  6502] execve("/bin/ls", ["ls", "-d", "-Q", "/etc/rc2.d/S20winbind"], [/* 21 vars */]) = 0
[pid  6503] execve("/usr/bin/xargs", ["xargs"], [/* 21 vars */]) = 0
[pid  6504] execve("/bin/echo", ["/bin/echo", "/etc/rc2.d/S20winbind"], [/* 21 vars */]) = 0
[pid  6507] execve("/usr/bin/xargs", ["xargs"], [/* 21 vars */] <unfinished ...>
[pid  6506] execve("/bin/ls", ["ls", "-d", "-Q", "/etc/rc2.d/K[0-9][0-9]winbind"], [/* 21 vars */]) = 0
[pid  6507] <... execve resumed> )      = 0
[pid  6508] execve("/bin/echo", ["/bin/echo"], [/* 21 vars */]) = 0
[pid  6510] execve("/bin/ls", ["ls", "-d", "-Q", "/etc/rcS.d/S[0-9][0-9]winbind"], [/* 21 vars */]) = 0
[pid  6511] execve("/usr/bin/xargs", ["xargs"], [/* 21 vars */] <unfinished ...>
[pid  6511] <... execve resumed> )      = 0
[pid  6512] execve("/bin/echo", ["/bin/echo"], [/* 21 vars */]) = 0
[pid  6513] execve("/etc/init.d/winbind", ["/etc/init.d/winbind", "start"], [/* 21 vars */]) = 0
[pid  6514] execve("/bin/mkdir", ["mkdir", "-p", "/var/run/samba/winbindd_privileg"...], [/* 21 vars */]) = 0
[pid  6515] execve("/bin/chgrp", ["chgrp", "winbindd_priv", "/var/run/samba/winbindd_privileg"...], [/* 21 vars */]) = 0
[pid  6516] execve("/bin/chmod", ["chmod", "0750", "/var/run/samba/winbindd_privileg"...], [/* 21 vars */]) = 0
[pid  6517] execve("/sbin/start-stop-daemon", ["start-stop-daemon", "--start", "--quiet", "--oknodo", "--exec", "/usr/sbin/winbindd", "--"], [/* 21 vars */]) = 0
[pid  6517] execve("/usr/sbin/winbindd", ["/usr/sbin/winbindd"], [/* 21 vars */]) = 0
[pid  6518] execve("/usr/bin/basename", ["basename", "/usr/sbin/invoke-rc.d"], [/* 21 vars */]) = 0
```

Thanks for the help!

---

### Post by happyhamster on 2010-10-11
Ok, so the file is /var/lib/dpkg/info/winbind.postinst. Could show the content of that file? (it could be corrupted somehow). Easy way of doing that is running:

```

cat /var/lib/dpkg/info/winbind.postinst
```

---

### Post by happyhamster on 2010-10-11
BTW, one other thing you should look into is if samba is installed correctly (samba-common). See:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/288496](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/288496)

---

### Post by w33k on 2010-10-12
Thanks for your help. Samba seemed to be the problem. From the bug page I tried

```
sudo dpkg-reconfigure samba-common

```and then

```
sudo dpkg --configure -a
```and this seems to have fixed it!

---

