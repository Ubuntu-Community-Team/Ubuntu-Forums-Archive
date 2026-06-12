---
title: "Ubuntu Server doesn't upgrade"
date: 2012-03-31
forum: General Help
---

### Post by Korn7 on 2012-03-31
Hello all,
I have a LAMP server and running Ubuntu Server 11.10 on it. I've got this error msg when I want to upgrade my box :)
```
root@ibhserver:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic linux-headers-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  libgudev-1.0-0 libudev0 linux-libc-dev udev
4 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/1,272 kB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by jerrrys on 2012-03-31
check this out

[http://cksum.org/blog/149-dpkg-warning-ldconfig-not-found-in-path-or-not-executable](http://cksum.org/blog/149-dpkg-warning-ldconfig-not-found-in-path-or-not-executable)

more here

[https://www.google.com/search?client=ubuntu&channel=fs&q=warning%3A+%27ldconfig%27+not+found+in+PATH+or+not+executable&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=warning%3A+%27ldconfig%27+not+found+in+PATH+or+not+executable&ie=utf-8&oe=utf-8)

---

### Post by Korn7 on 2012-03-31
Yes. Before I do this post, I've Googled but none works for me :)
This problem occurred after installing some security apps. But I'm not sure exactly which one is!
I just want to know another way to find "What is the problem".

---

### Post by Korn7 on 2012-03-31
I solved the problem by copying /etc/ldconfig from another Ubuntu to mine and now works fine! ldconfig file for those who have same problem:
```
#!/bin/sh

if  test $# = 0                            \
    && test x"$LDCONFIG_NOTRIGGER" = x                \
 && test x"$DPKG_MAINTSCRIPT_PACKAGE" != x            \
 && dpkg-trigger --check-supported 2>/dev/null            \
 && dpkg --compare-versions "$DPKG_RUNNING_VERSION" ge '1.14.5ubuntu10~~'
then
    if dpkg-trigger --no-await ldconfig; then
        if test x"$LDCONFIG_TRIGGER_DEBUG" != x; then
            echo "ldconfig: wrapper deferring update (trigger activated)"
        fi
        exit 0
    fi    
fi

exec /sbin/ldconfig.real "$@"

```
Don't forget to execute permission "chmod +x /sbin/ldconfig" :)

---

### Post by dcstar on 2012-03-31
> **Korn7 said:**
> I solved the problem
.........

Then MARK the thread!

---

