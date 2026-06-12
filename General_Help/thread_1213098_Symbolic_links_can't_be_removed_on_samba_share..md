---
title: "Symbolic links can't be removed on samba share."
date: 2009-07-14
forum: General Help
---

### Post by yupper on 2009-07-14
I have a CIFS share mounted from a Samba server (running Red Hat 5.2) on my Ubuntu 8.04 desktop.  I can create symbolic links, but not remove them.  

```

% ls
file1
%  ln -s file1 link2file1
% ls -l
-rw-r--r-- 1 jhazen jhazen 24 Jul 14  2009 file1
lrwxrwxrwx 1 jhazen jhazen  5 Jul 14  2009 link2file1 -> file1
% rm link2file2
% ls -l
-rw-r--r-- 1 jhazen jhazen 24 Jul 14  2009 file1
lrwxrwxrwx 1 jhazen jhazen  5 Jul 14  2009 link2file1 -> file1

```I'm aware that both ends of the connection must support the Samba unix extensions.  The Samba server supports the unix extensions (by default).  Likewise, the Samba unix extensions on my desktop are enabled (there is "1" in [FONT=Lucida Console]/proc/fs/cifs/LinuxExtensionsEnabled).

[/FONT]Has anyone else experienced the problem?

p.s. I can read and write ordinary files on the share without any trouble.

---

