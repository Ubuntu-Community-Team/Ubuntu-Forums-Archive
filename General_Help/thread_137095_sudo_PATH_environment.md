---
title: "sudo PATH environment"
date: 2006-02-27
forum: General Help
---

### Post by foxy123 on 2006-02-27
it looks like 'sudo' uses a different PATH environment comparing to a user. I am trying to install a xffm file manager from svn on xfce4-svn, which is in /opt. Xffm has an installation script which does ./autogen.sh, make and make install for all modules. The problem is that is I run the script as a user it does not have enough permissions to install the thing, but if I try to run it with 'sudo' it cannot find development libraries from /opt.

---

### Post by piedamaro on 2006-02-27
Try sudo -s -h to get more env variables exported.
Or you can 
export LD_LIBRARY_PATH
to poinmt where your libs live under /opt
Hope this heps.

---

### Post by foxy123 on 2006-02-27
It is quite strange, because LD_LIBRARY_PATH is exported in the script which launches xfce4-svn:
```
#!/bin/bash

xfce_prefix="/opt/xfce4-svn"
xfce_sysconfdir="/opt/xfce4-svn/etc"

export PATH="${xfce_prefix}/bin:${PATH}"
export LD_LIBRARY_PATH="${xfce_prefix}/lib:${LD_LIBRARY_PATH}"
export PKG_CONFIG_PATH="${xfce_prefix}/lib/pkgconfig:${PKG_CONFIG_PATH}"

test -z "${XDG_DATA_DIRS}" && XDG_DATA_DIRS="/usr/local/share:/usr/share"
export XDG_DATA_DIRS="${xfce_prefix}/share:${XDG_DATA_DIRS}"

test -z "${XDG_CONFIG_DIRS}" && XDG_CONFIG_DIRS="/etc/xdg"
export XDG_CONFIG_DIRS="${xfce_sysconfdir}/xdg:${XDG_CONFIG_DIRS}"

exec "${xfce_prefix}/bin/startxfce4"

```

if I look up the path it gives me a proper path:

```
:~$ $PATH
bash: /opt/xfce4-svn/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games: No such file or directory

```

however in sudo environment the path does not include /opt/xfce4-svn:

```
$ sudo -s
root@neclaptop:~/CVS/xfce4-svn-source/xffm/fgr# $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: No such file or directory

```
how to put /opt/xfce4-svn into root's path?

---

### Post by piedamaro on 2006-02-28
You need root jprivileges ust before make install, you don't need them to compile. But make install could invoke the linker so you 're stuck with the same problem. Then...
Open a root shell (sudo -s) then export your LD_LIBRARY_PATH variable. Like this:
sudo -s
export LD_LIBRARY_PATH="/opt/xfce4-svn/lib:${LD_LIBRARY_PATH}"

and, don't ever try to declare LD_LIBRARY_PATH in your bash startup script and try to have few entry in /etc/ld.so.conf too (/lib and /usr/lib are always included). If you do _every_ program you run will search those directories to find shared libs thus increasing startup time.
Ah and $PATH is the path for binaries not shared libraries.
Hope this helps.

---

