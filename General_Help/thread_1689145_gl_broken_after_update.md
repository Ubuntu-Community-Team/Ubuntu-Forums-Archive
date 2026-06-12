---
title: "gl broken after update"
date: 2011-02-16
forum: General Help
---

### Post by klakin on 2011-02-16
I uppdated my 10-4 lts this morning and now nothing that uses open gl works.

I get this error:
error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

It worked fine before the update.

Here is the update history from this morning:

Commit Log for Wed Feb 16 08:04:50 2011


Upgraded the following packages:
google-chrome-stable (9.0.597.94-r73967) to 9.0.597.98-r74359
language-pack-en (1:10.04+20100714) to 1:10.04+20110204
language-pack-en-base (1:10.04+20100714) to 1:10.04+20110204
language-pack-gnome-en (1:10.04+20100714) to 1:10.04+20110204
language-pack-gnome-en-base (1:10.04+20100714) to 1:10.04+20110204
libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.4) to 1.8.1+dfsg-2ubuntu0.6
libk5crypto3 (1.8.1+dfsg-2ubuntu0.4) to 1.8.1+dfsg-2ubuntu0.6
libkrb5-3 (1.8.1+dfsg-2ubuntu0.4) to 1.8.1+dfsg-2ubuntu0.6
libkrb5support0 (1.8.1+dfsg-2ubuntu0.4) to 1.8.1+dfsg-2ubuntu0.6

So one of those packages has to have broken it.

Thank you

---

### Post by win2456 on 2011-03-06
This is how I fixed my issue:

```
sudo apt-get install libgl1-mesa-glx --reinstall
```

---

