---
title: "wput command help"
date: 2011-06-07
forum: General Help
---

### Post by RFRFG on 2011-06-07
i recently put this command into my rc.local:


wput /home/heather/.logs/log.log [ftp://a5843072: (password) @tdoui.netau.net/](ftp://a5843072: (password) @tdoui.netau.net/)

i wanted to have this file hosted on the internet and automatically updated every time i login, but it fails to work in rc.local

it works manually in the terminal, but i can't get it to transfer on startup

i have other commands in rc.local that work fine

any help would be nice

---

### Post by blueridgedog on 2011-06-07
Are there any errors in your logs?  Have you tried it with a full path to wput in the rc.local file?

---

### Post by RFRFG on 2011-06-07
how do i find the error logs? i'm relatively new to ubuntu commands. and is that not the full path?

---

### Post by blueridgedog on 2011-06-07
For the log:

```
cat /var/log/messages
```

or 

```
tail /var/log/messages
```

The command is

```
/usr/bin/wput
```

---

