---
title: "Python3 ssl support in lucid"
date: 2010-12-31
forum: General Help
---

### Post by defue on 2010-12-31
Hi,

I am running ubuntu lucid lynx 10.4 and doubt how to enable ssl support in python3.

The following python code says me that I have no ssl support (taken from xmlrpc/client.py):
```
if not hasattr(socket, "ssl"):
            raise NotImplementedError(
                "your version of http.client doesn't support HTTPS")

```
What package I need to install to make it work?

Thanks and happy new year :)

---

### Post by defue on 2011-01-08
I've found out the reason myself. It is python3 bug that is going to be fixed in 3.1.3. See [this]("http://bugs.python.org/issue9991") for details.

---

