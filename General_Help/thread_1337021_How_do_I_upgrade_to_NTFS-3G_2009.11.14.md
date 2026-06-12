---
title: "How do I upgrade to NTFS-3G 2009.11.14?"
date: 2009-11-25
forum: General Help
---

### Post by godmode117 on 2009-11-25
Anyone know? The version i currently have is 2009.2.1. Synaptic isn't doing anything for me.I hear the newest version helps lower CPU usage.

---

### Post by hal10000 on 2009-11-25
If you don't find a debian package, then i guess you have to download the source code and compile it yourself.

Sometimes even a debian package (if it's not for ubuntu) can not be installed because of missing dependencies.

---

### Post by ib.lundgren on 2009-11-25
Citing ntfs-3g.org > Most distributions includes and uses NTFS-3G. Please use that one unless it's an old version.

If you want the bleeding edge then a simple (knock on wood, <insert possible disaster here>) 
```
./configure
make
sudo make install
```
should do the trick.

Source tarball found here [http://www.ntfs-3g.org/ntfs-3g-2009.11.14.tgz]("http://www.ntfs-3g.org/ntfs-3g-2009.11.14.tgz")

---

### Post by godmode117 on 2009-11-25
Well thanks for the input guys. I think I'll just stick with the version I have. :p

---

### Post by Ferux on 2010-04-19
According to the number of threads arround this issue, and the number of bug reports, I think this is an important problem.


I tried what was suggested and what was carried out in [another thread]("http://ubuntuforums.org/showthread.php?t=1362726"): compiling the 2009.11.14 version. I downloaded the file from the official link as stated in this thread.

When doing 'make', I get following errors (my Ubuntu speaks Flemmish, I'm sorry...):

```

filixandra@PC5:~/Brol/ntfs-3g-2009.11.14$ make
make  all-recursive
make[1]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14' wordt binnengegaan
Making all in include
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include' wordt binnengegaan
Making all in ntfs-3g
make[3]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include/ntfs-3g' wordt binnengegaan
make[3]: Er hoeft niets gedaan te worden voor 'all'.
make[3]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include/ntfs-3g' wordt verlaten
Making all in fuse-lite
make[3]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include/fuse-lite' wordt binnengegaan
make[3]: Er hoeft niets gedaan te worden voor 'all'.
make[3]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include/fuse-lite' wordt verlaten
make[3]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include' wordt binnengegaan
make[3]: Er hoeft niets gedaan te worden voor 'all-am'.
make[3]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include' wordt verlaten
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/include' wordt verlaten
Making all in libfuse-lite
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/libfuse-lite' wordt binnengegaan
make[2]: Er hoeft niets gedaan te worden voor 'all'.
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/libfuse-lite' wordt verlaten
Making all in libntfs-3g
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/libntfs-3g' wordt binnengegaan
make[2]: Er hoeft niets gedaan te worden voor 'all'.
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/libntfs-3g' wordt verlaten
Making all in src
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/src' wordt binnengegaan
gcc -DHAVE_CONFIG_H -I. -I..     -I../include/ntfs-3g -g -O2 -Wall -MT ntfs_3g_secaudit-secaudit.o -MD -MP -MF .deps/ntfs_3g_secaudit-secaudit.Tpo -c -o ntfs_3g_secaudit-secaudit.o `test -f 'secaudit.c' || echo './'`secaudit.c
secaudit.c:262:24: error: attr/xattr.h: Bestand of map bestaat niet
secaudit.c: In function &#8216;showmounted&#8217;:
secaudit.c:5033: warning: implicit declaration of function &#8216;getxattr&#8217;
make[2]: *** [ntfs_3g_secaudit-secaudit.o] Fout 1
make[2]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14/src' wordt verlaten
make[1]: *** [all-recursive] Fout 1
make[1]: Map '/home/filixandra/.local/share/Trash/files/ntfs-3g-2009.11.14' wordt verlaten
make: *** [all] Fout 2

```

Btw, 'Fout' means 'Fault' and 'Bestand of map bestaat niet' means 'File or folder doesn't exist'.

Anyone an idea?

Thanks

---

