---
title: "setting global network proxy settings?"
date: 2011-06-14
forum: General Help
---

### Post by TheHimself on 2011-06-14
I think there is an application which lets you set the proxy settings for *all* applications. I remember seeing something like this in Gnome's network menu but now I'm using XFCE.

---

### Post by Toz on 2011-06-14
The code that needs to be added is:
```
export http_proxy="http://user:password@proxyserver:port"
export https_proxy="http://user:password@proxyserver:port"
export ftp_proxy="http://user:password@proxyserver:port"
```
*The user and password fields are optional and are only necessary if you need to authenticate into the proxy.

If you are using the bash shell (default):
- If the proxy settings are for the current user only, then they should be added to **~/.bashrc**
- If they are intended to be system-wide, then add them to **/etc/bash.bashrc**

If you are using another shell, you will need to add it to the appropriate configuration files for that shell.

---

