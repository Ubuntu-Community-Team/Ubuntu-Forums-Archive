---
title: "opendchub almost working!"
date: 2010-01-18
forum: General Help
---

### Post by coffinzm on 2010-01-18
Ubuntu 9.10
I have an installation of opendchub up and running, and users are able to connect and chat.  However, users are unable to download each others' filelists.  I've looked at opendchub's output at its most verbose level, and it looks like things should be working.  

Here's some of that output:
```

Dec 19 23:24:54 PID: 2094 Received command from XXX.XXX.XXX.XX, type 0x8: $ConnectToMe zach XXX.XXX.XXX.XX:1412|$ConnectToMe zach XXX.XXX.XXX.XX:1412|
Dec 19 23:24:54 PID: 2093 Received command from forked_process, type 0x80: $Script data_arrival ^E^Ebstern^E^E$ConnectToMe zach XXX.XXX.XXX.XX:1412|$Script data_arrival ^E^Ebstern^E^E$ConnectToMe zach XXX.XXX.XXX.XX:1412|
Dec 19 23:25:12 PID: 2094 Received command from XXX.XXX.XXX.XX, type 0x8: $ConnectToMe bstern XXX.XXX.XXX.XX:1412|
Dec 19 23:25:12 PID: 2093 Received command from forked_process, type 0x80: $Script data_arrival ^E^Ezach^E^E$ConnectToMe bstern XXX.XXX.XXX.XX:1412|

```

IPs have been Xed out by me.

Messages from within the DC++ client, Shakespeer on OS X look good too.
Any ideas?

---

### Post by cristofaro on 2010-02-10
I have the same issue with opendchub.  Can connect to the hub but no users are able to download filelists. I have tried various clients and computers which makes me pretty sure it is some problem with my hub config.

---

### Post by cristofaro on 2010-02-10
bump

I have a Windows computer on the network which I installed YnHub on. Without changing client settings on any computers on the network (other than ip and port :P) users were able to download files fine and have had no trouble getting filelists. Again seems to be related to the way opendchub has been configured.

---

