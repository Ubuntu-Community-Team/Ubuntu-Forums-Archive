---
title: "Problem on Lucid: segfault when running dropboxd"
date: 2010-05-20
forum: General Help
---

### Post by janesconference on 2010-05-20
(sorry, I'm, new, don't know if this is the correct section).



I'm using the .deb package for Ubuntu  (nautilus-dropbox_0.6.2_i386.deb). I have Lucid.
When I start the installer from the menu (it invokes /usr/bin/python  /usr/bin/dropbox start -i), I see a zombie process with ps aux (  [dropbox] <defunct>). By the way, the installer downloads the  daemon and extracts it. Then, it dies.
 If I go in .dropbox-dist directory and strart ./dropboxd, it gives me  a segmentation fault, and /var/log/syslog reads:


```
kernel: [ 8243.166661] dropbox[6202]: segfault at 2f8 ip  001af5e2 sp bfcd34e8 error 4 in libpthread.so.20.0.27[1a7000+14000]

```
Everytime it segfaults.


 I tried to start the daemon with strace, and the last lines are  always like that:
 ```
clone(child_stack=0xb7686494, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb7686bd8, {entry_number:6, base_addr:0xb7686b70, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb7686bd8) = 6268
futex(0x963bcf8, FUTEX_WAKE_PRIVATE, 1) = 1
select(0, NULL, NULL, NULL, {0, 0})     = 0 (Timeout)
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = 0
futex(0x963bcf8, FUTEX_WAKE_PRIVATE, 1) = 1
futex(0x963bcf8, FUTEX_WAIT_PRIVATE, 0, NULL) = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1274349344, 162584}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
``` Anyone had this problem?

---

### Post by golbasche2 on 2010-05-21
I get the same exact problem.  I don't know why.

---

### Post by janesconference on 2010-05-24
> **golbasche2 said:**
> I get the same exact problem.  I don't know why.
I posted the problem there, also: [http://forums.dropbox.com/topic.php?id=20204&replies=11#post-127865](http://forums.dropbox.com/topic.php?id=20204&replies=11#post-127865)
You could add something about your configuration and dropbox dvelopers hopefully will sort the issue out.

---

### Post by dino99 on 2010-05-24
add this ppa into synaptic repo then update :

[https://launchpad.net/~emergya/+archive/ppa](https://launchpad.net/~emergya/+archive/ppa)

---

### Post by janesconference on 2010-05-24
> **dino99 said:**
> add this ppa into synaptic repo then update :

[https://launchpad.net/~emergya/+archive/ppa]("https://launchpad.net/%7Eemergya/+archive/ppa")

I did, and I've got the same problem. The problem is not in the .deb, but in the dropbox-proprietary daermon server.

---

