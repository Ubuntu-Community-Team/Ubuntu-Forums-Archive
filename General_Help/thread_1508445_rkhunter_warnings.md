---
title: "rkhunter warnings"
date: 2010-06-13
forum: General Help
---

### Post by grumpy.biatch on 2010-06-13
Hi,

What is the significance and ramifications of rkhunter warnings at following locations.

    /bin/bash                                                [ Warning ]
    /bin/cat                                                 [ Warning ]
    /bin/chmod                                               [ Warning ]
    /bin/chown                                               [ Warning ]
    /bin/cp                                                  [ Warning ]
    /bin/date                                                [ Warning ]
    /bin/df                                                  [ Warning ]
    /bin/dmesg                                               [ Warning ]
    /bin/echo                                                [ Warning ]
    /bin/ed                                                  [ Warning ]
    /bin/egrep                                               [ Warning ]
    /bin/fgrep                                               [ Warning ]
    /bin/fuser                                               [ Warning ]
    /bin/grep                                                [ Warning ]
    /bin/ip                                                  [ Warning ]
    /bin/kill                                                [ Warning ]
    /bin/less                                                [ Warning ]
    /bin/login                                               [ Warning ]
    /bin/ls                                                  [ Warning ]
    /bin/lsmod                                               [ Warning ]
    /bin/mktemp                                              [ Warning ]
    /bin/more                                                [ Warning ]
    /bin/mount                                               [ Warning ]
    /bin/mv                                                  [ Warning ]
    /bin/netstat                                             [ Warning ]
    /bin/ps                                                  [ Warning ]
    /bin/pwd                                                 [ Warning ]
    /bin/readlink                                            [ Warning ]
    /bin/sed                                                 [ Warning ]
    /bin/sh                                                  [ Warning ]
    /bin/su                                                  [ Warning ]
    /bin/touch                                               [ Warning ]
    /bin/uname                                               [ Warning ]
    /bin/which                                               [ Warning ]
    /bin/dash                                                [ Warning ]

---

### Post by grumpy.biatch on 2010-06-13
Hi,

Resolved it by doing  "sudo rkhunter --propupd". 

If you run bleachbit as a root after system updates please do sudo  rkhunter --propupd after it.

Best,

David

---

