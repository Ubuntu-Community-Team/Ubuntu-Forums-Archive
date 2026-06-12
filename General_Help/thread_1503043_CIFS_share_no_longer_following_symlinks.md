---
title: "CIFS share no longer following symlinks"
date: 2010-06-06
forum: General Help
---

### Post by killcast on 2010-06-06
I just made the upgrade to 10.04 over the weekend, and everything seems to be working fine, minus one nagging detail.

I have a Mythbuntu setup - a frontend and a backend.  In addition to recording television, I have a folder setup on my backend where I can dump movie files to watch on the frontend.  The folder is shared in the /etc/fstab via a CIFS share.  Within that folder is a symlink to where my torrent folder is located.  The issues seems to be how my frontend handles symlinks within the shared folders.  If I run "ls -la" in my base CIFS share folder, it lists the symlink folder and says it's owned by root, but if I try and change to that directory - either using "ls" or "cd" - it says Permission Denied.  On the backend, I changed ownership of the symlink to the username the CIFS is using to login, but that had no effect.  I'm not familiar with how to do any sort of configuration on CIFS, if that's where I'd even need to start.

Any help would be appreciated.

---

### Post by Morbius1 on 2010-06-06
The symlink change to samba happened because of a security issue: [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

To  restore it to it's old operation you could try this:

Add the  following lines to the [global] section of smb.conf:
```
follow  symlinks = yes
wide links = yes
unix extensions = no
```Then  restart the samba service

---

### Post by killcast on 2010-06-10
Apologies for the delay in response, as I was out of town for a few days.

Thank you very much for the response.  I checked out smb.conf, and the settings were missing on my frontend, but had already been added to my backend.  I restarted the samba service on both.  What appears to be happening is that if I move to the folder that is being shared, and use the "ls -la" command, it seems to alternate between displaying the folder as:

```
drwxrwxrwx 0 root root    0 2010-06-05 16:17 TorrentFiles
```

and: 

```
ls: cannot access TorrentFiles: Permission denied
```
```
d????????? ? ?    ?       ?                ? TorrentFiles
```

It alternates regularly back and forth between those two responses.  Thoughts?

---

