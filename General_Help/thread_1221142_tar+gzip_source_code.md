---
title: "tar+gzip source code"
date: 2009-07-23
forum: General Help
---

### Post by ralphrost on 2009-07-23
Hello all,
 
I need to develop an application that deals with tar.gz files, so I need to understand the file format.
 
I'd like to have the source code that has the struct (a header) in which a tar.gz file is build into. Would you know where can I find this on Ubuntu?
 
Thank you
 
Ralph

---

### Post by michy99 on 2009-07-23
You can get the tar source code from:

[http://savannah.gnu.org/projects/tar](http://savannah.gnu.org/projects/tar)

---

### Post by unutbu on 2009-07-23
This shows you the package which provides the tar and gzip programs:
```
% dpkg -S $(which tar)
tar: /bin/tar
% dpkg -S $(which gzip)
gzip: /bin/gzip
```

To download the source code, simply run:
```

apt-get source tar
apt-get source gzip
```

(Be sure you to have the source repositories enabled in System>Admin>Software Sources.)

---

