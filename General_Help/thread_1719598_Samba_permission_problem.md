---
title: "Samba permission problem"
date: 2011-04-02
forum: General Help
---

### Post by umsorg on 2011-04-02
When I create a file to local partition the permissions are:

```
Owner: read & write
Group: read & write
Others: None
```When I create a file to samba share the permissions are:

```
Owner: read & write
Group: read
Others: None
```I have added stuff to smb.conf:

```
create mask = 0777
directory mask = 0777
force create mask = 0777
force directory mode = 0777
```How can fix that the permissions for samba share are same than local?

```
Owner: read & write
Group: read & write
Others: None
```

---

### Post by HermanAB on 2011-04-02
Here is a debug guide:
[http://www.aeronetworks.ca/howtos/samba-debug-howto.html](http://www.aeronetworks.ca/howtos/samba-debug-howto.html)

---

