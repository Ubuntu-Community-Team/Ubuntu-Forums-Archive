---
title: "Samba fails &quot;able to open configuration file&quot;"
date: 2010-02-23
forum: General Help
---

### Post by bigred1 on 2010-02-23
I just reinstalled Karmic. I tried to share a folder, and got a message that I had to install the Windows sharing functionality. I did so, but now I get this error when I try to share a directory, with our without write permissions. 

How do I fix this?

```
Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services.
```

---

### Post by Morbius1 on 2010-02-23
This is just a guess but maybe it installed samba but didn't start the samba service.

In a Terminal type: **sudo service samba restart**

---

### Post by bigred1 on 2010-02-23
Thanks -- however, that didn't fix it. The messages showed that the daemon was already running and after this restart the same error occurred.

```
 
* Stopping Samba daemons                                                [ OK ] 
* Starting Samba daemons                                                [ OK ]
```

---

### Post by BbUiDgZ on 2010-02-23
you might wanna [RTM](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

---

### Post by bigred1 on 2010-02-23
It turns out to be a real bug in Samba, but one which is fixed in the latest update. 

In Syntaptic, samba-commons is marked for upgrade. 

Upgrade, and the sharing works.

---

