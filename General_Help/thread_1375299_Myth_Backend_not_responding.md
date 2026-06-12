---
title: "Myth Backend not responding"
date: 2010-01-07
forum: General Help
---

### Post by yelloguy on 2010-01-07
I have a mythtv box running mythbackend that I have been using for several months.  I use Mythweb for most admin and mythfrontend running on an iMac for watching recordings (and an Acer Revo running XBMC).

I watched some recording on XBMC without issues last night and this afternoon, when I started mythfrontend, it complained that mythbackend cannot be reached at <ip><port>.  So I tried it from mythweb.  I can see the UI for mythweb but when I try to get Listings, Recordings or anything that needs backend, it complains with the same message.

I have tried restarting the myth backend computer.  Everything came back up normal but the problem was still present.

I have tried restarting mythbackend.  It stops and starts up normally.  But doesn't fix the problem.

I have tried connecting to mysql.  I can connect and query tables just fine.  I can see the IP and port are setup correctly.  But I still have the problem.

I can reach the shares on the box without any problems so I can play the recordings as mpeg files.

But I am not sure why mythtv backend is not responding.  Is there something else I can check?

Thanks in advance.
PS: The exact error is:
```

Error

Unable to connect to the master backend at 192.168.0.14:6543.
Is it running?

```

---

