---
title: "Mounting davfs giving ssl handshake failed error"
date: 2011-03-21
forum: General Help
---

### Post by chavodel8 on 2011-03-21
I'm trying to connect to a webdav server with very poor luck. My preference would be to mount it to my file system, but simply connecting with Cadaver would be fine too.

I've tried:
```

mparks@mparks:~$ sudo mount -t davfs https://<host>:<port>/<path> /media/webdrives/<mount-dir>
[sudo] password for mparks: 
Please enter the username to authenticate with server
https://<host>:<port>/<path> or hit enter for none.
  Username: <username>
Please enter the password to authenticate user handbook with server
https://<host>:<port>/<path> or hit enter for none.
  Password: <password>
/sbin/mount.davfs: Mounting failed.
SSL handshake failed: Secure connection truncated

```


In some config file (and now I can't seem to find it again) (EDIT: in /etc/fstab) I added a line with the webdav server url, the local path to where I want to mount it, and some other little configs. It allowed me to simply type: "sudo mount /media/webdrives/<mount-dir>" instead of typing in the whole URL every time. I still see the same results as above.

I tried a suggestion to add 'dav_group users' to my /etc/davfs2/davfs2.conf file. Same error.

I've tried the suggestion at the end of [this]("http://ubuntuforums.org/showthread.php?t=1634609&page=2&highlight=davfs") thread. I type:
'sudo ./fusedav https://<host>:<port>/<path> /media/webdrives/<mount-dir>' and it just hangs. Nothing seems to happen at all.

I've tried using Cadaver.
```

mparks@mparks:~$ cadaver https://<host>:<port>/<path>
Could not open collection:
SSL handshake failed: Secure connection truncated
dav:/<path>/? exit
mparks@mparks:~$ 

```

Most searches for this error show results related to svn. This, as far as I know, has utterly nothing to do with subversion. I'm simply trying to access a webdav server either by client or by file-system mount.

Any tips or help would be much appreciated.

Thank you!

---

### Post by chavodel8 on 2011-03-21
Are there any logs that the above commands produce? I'm not aware of any, but if so, that might prove useful.

Also, if there's any further information I can/should add, I'd be happy to. Please just let me know what you need.

Thanks again!

---

### Post by chavodel8 on 2011-03-21
Oh my. :oops: :roll:

I didn't realize that using https was an assumption on my part. I didn't need the TLS - just used http and everything went swimmingly.

I was never here. You never saw me.

---

