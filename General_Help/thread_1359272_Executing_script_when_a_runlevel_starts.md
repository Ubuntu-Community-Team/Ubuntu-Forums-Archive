---
title: "Executing script when a runlevel starts"
date: 2009-12-19
forum: General Help
---

### Post by GagleKas on 2009-12-19
Hi.

How can I execute a script when a runlevel starts, for example telinit 4. The script is:
```
#! /bin/bash
exec /home/my_user/file
```Thanks.

---

### Post by dcstar on 2009-12-19
> **GagleKas said:**
> Hi.

How can I execute a script when a runlevel starts, for example telinit 4. 

The same way as every single other script that each runlevel processes is done.

If you do a web search there should be hundreds of detailed posts on how to do such things.

---

