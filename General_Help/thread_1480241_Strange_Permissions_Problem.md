---
title: "Strange Permissions Problem"
date: 2010-05-11
forum: General Help
---

### Post by difster on 2010-05-11
I'm having a permissions problem with Ubuntu and apache.

There are two users, I'll just call them A and B.

All of the files belong to A and group root. I'm logged in as B and I have admin privileges. My website is working just fine but when I create a directory in the web root, change the owner to A on the directory and all files I still get a Permission Denied error when I try to access it from the web. I've also set permissions to rxwr-xr-x on the directory and all the files. So I don't understand what's going on. Why am I still getting a permission denied error?

All help is appreciated!

---

### Post by cdenley on 2010-05-11
The server section would be a more appropriate place for anything involving apache. What is the local filesystem path to the file requested? What is the URL you are using when attempting to access it? What shows up in /var/log/apache2/error.log?
```

tail /var/log/apache2/error.log

```

---

