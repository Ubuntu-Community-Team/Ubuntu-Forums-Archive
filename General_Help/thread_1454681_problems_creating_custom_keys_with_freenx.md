---
title: "problems creating custom keys with freenx"
date: 2010-04-15
forum: General Help
---

### Post by r.lopez.negrete on 2010-04-15
Hi all,

I just installed freenx in ubuntu 9.10, and I want to setup custom keys. However I'm having problems generating them. First I had this error

```
update-rc.d: warning: freenx-server stop runlevel arguments (1) do not match LSB Default-Stop values
```

I modified /var/lib/dpkg/info/freenx-server.postinst, the line that read 

```
update-rc.d freenx-server start 20 2 3 4 5 . stop 99 1 . >/dev/null
```

to

```
update-rc.d freenx-server start 20 2 3 4 5 . stop 99 0 1 6 . >/dev/null
```

This eliminates the previous error, however the custom_key folder mentioned [here]("https://help.ubuntu.com/community/FreeNX#Using custom SSH keys") is not generated.

Any ideas??

Thanks
 R

---

### Post by 2hot6ft2 on 2010-04-15
Go thru the guide in my signature below, its step by and I would start by undoing what ever you have done. Or if you think it will still work with your changes pick it up from the FreeNX section of the guide. The instructions for generating the FreeNX keys is a little different.

---

