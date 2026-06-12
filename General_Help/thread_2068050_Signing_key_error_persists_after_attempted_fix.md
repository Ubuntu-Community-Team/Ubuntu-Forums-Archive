---
title: "Signing key error persists after attempted fix"
date: 2012-10-08
forum: General Help
---

### Post by Tony1337 on 2012-10-08
When running sudo apt-get update, I get the following:

```
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

I have attempted the following, as suggested by several help sites:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

I have run sudo apt-get upgrade as well as rebooted. However, I still get the same signing key error.

---

### Post by albandy on 2012-10-08
Change your repository server:
go to software center

Select edit --> software source (or something like that, I'm translating from spanish)

and in Download from select main server or primary server.

then test again if works.

---

### Post by Tony1337 on 2012-10-08
I changed from "Server for United States" to "Main server" and there is no longer an error, thanks. I then changed it back to "Server for United States" and there is still no error. What do you think solved the problem?

---

### Post by albandy on 2012-10-08
Probably  keys are updated when you choose other sources.

---

