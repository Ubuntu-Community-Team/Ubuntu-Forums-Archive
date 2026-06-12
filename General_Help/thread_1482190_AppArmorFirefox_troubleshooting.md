---
title: "AppArmor/Firefox troubleshooting"
date: 2010-05-13
forum: General Help
---

### Post by doas777 on 2010-05-13
howdy all,

I enabled the Firefox AppArmor profile yesterday, but now when i go to ArsTechnica.com, my browser crashes. 

here is the terminal output:
```
karmic:~$ firefox

(firefox:1689): GLib-WARNING **: g_set_prgname() called multiple times
2.4+ kernel w/o ELF notes? -- report this
Segmentation fault
```and here is the dmesg, clearly showing that it is an apparmor problem:
```

[ 3047.707162] type=1503 audit(1273762204.800:26): operation="file_mmap" pid=1689 parent=1685 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::mr" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/local/lib/libidn.so.11.6.1"
[ 3047.708831] type=1503 audit(1273762204.804:27): operation="file_mmap" pid=1689 parent=1685 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::mr" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/local/lib/libidn.so.11.6.1"
[ 3047.709391] type=1503 audit(1273762204.804:28): operation="file_mmap" pid=1689 parent=1685 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::mr" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/local/lib/libidn.so.11.6.1"
[ 3047.709941] type=1503 audit(1273762204.804:29): operation="file_mmap" pid=1689 parent=1685 profile="/usr/lib/firefox-3.5.*/firefox" requested_mask="::mr" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/local/lib/libidn.so.11.6.1"

```so how would you go about allowing these actions in firefox?

---

