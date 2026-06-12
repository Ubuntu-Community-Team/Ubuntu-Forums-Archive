---
title: "selinux problem in ubuntu10.10 64bit support"
date: 2011-02-11
forum: General Help
---

### Post by ashish_agrawal on 2011-02-11
I am using ubuntu 10.10 64bit support:

 semanage permissive -a httpd_t
Traceback (most recent call last):
  File "/usr/sbin/semanage", line 460, in <module>
    process_args(sys.argv[1:])
  File "/usr/sbin/semanage", line 363, in process_args
    OBJECT.add(target)
  File "/usr/lib/pymodules/python2.6/seobject.py", line 275, in add
    os.chdir(dirname)
OSError: [Errno 2] No such file or directory: '/var/lib/selinux'

kindly let me know about this issue as earliest possible.

---

### Post by Joeb454 on 2011-02-11
*Thread moved to **General Help**.*

---

