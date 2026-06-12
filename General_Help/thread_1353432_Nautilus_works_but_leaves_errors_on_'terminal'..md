---
title: "Nautilus works but leaves errors on 'terminal'."
date: 2009-12-12
forum: General Help
---

### Post by Silvernail on 2009-12-12
This is on a brand new install. What have I not done? Do I need 'samba'? I have been to Systems > Administration > Users & Groups. I am the owner of the computer.


Sorry for the long quote:
> dafy@dafy:~$ sudo nautilus

** (nautilus:8311): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///root
......................................................................
............................................
..................

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:8488): Eel-WARNING  "nautilus-metafile.c: metafiles" hash table still has 15 elements at quit time (keys above)

(nautilus:8488): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 15 elements at quit time
dafy@dafy:~$ 


---

