---
title: "Segmentation fault ssh"
date: 2011-04-06
forum: General Help
---

### Post by aleister crowley on 2011-04-06
When I try connect by ssh i receive:
```
alester@dtbd13:~$ ssh alester@zapserver
ssh: /usr/local/zend/lib/libcrypto.so.0.9.8: no version information available (required by ssh)
**[COLOR="Red"]Segmentation fault[/COLOR]**

```

In my /var/log/messages, there is:
```
Apr  6 15:50:47 dtbd13 kernel: [ 4417.888483] ssh[3021]: **segfault at **1f00000060 ip 00007f686bdf3052 sp 00007fff9a1274a8 error 4 in libc-2.11.1.so[7f686bd70000+17a000]

```

If I gdb ssh:
```
Reading symbols from /usr/bin/ssh...(no debugging symbols found)...done.
(gdb) run alester@zapserver
Starting program: /usr/bin/ssh alester@zapserver
/usr/bin/ssh: /usr/local/zend/lib/libcrypto.so.0.9.8: no version information available (required by /usr/bin/ssh)
[Thread debugging using libthread_db enabled]

[COLOR="Blue"]Program received signal SIGSEGV, Segmentation fault.
__strlen_sse2 () at ../sysdeps/x86_64/multiarch/../strlen.S:31
31      ../sysdeps/x86_64/multiarch/../strlen.S: No such file or directory.
        in ../sysdeps/x86_64/multiarch/../strlen.S[/COLOR]
```

[SIZE="2"]**What's going on?**[/SIZE]

---

### Post by aleister crowley on 2011-04-06
The version of /usr/local/zend/lib/libcrypto.so.0.9.8 and /usr/local/zend/lib/libssl.so.0.9.8 were different from openssh installed.

---

### Post by kervin on 2011-06-14
How do we resolve this issue? I got the same problem... :(

---

### Post by MacinViLLe on 2011-06-22
How was this issue resolved? it was just tagged as resolved without the real answer...only the cause was given..

How did you resolved the issue? I encountered this after installing Zend Server CE and right after I restarted the system, this problem occurred.

Please be kind enough to share your solution.

Thanks!

---

### Post by MacinViLLe on 2011-06-23
Actually, it is just the libcrypto.so.0.9.8 that is causing trouble in my case. So I just removed it.

[Click here]("http://macinville.blogspot.com/2011/06/solving-ssh-segmentation-fault.html") to view the details how I solved this issue with my Natty Narwhal.

---

