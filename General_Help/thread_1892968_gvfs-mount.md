---
title: "gvfs-mount"
date: 2011-12-09
forum: General Help
---

### Post by kamaji792 on 2011-12-09
I am having trouble with **gvfs-mount**; run from the command line or as part of a script.

It always has been a bit unreliable but recently it has completely given up.  So if I try and mount a Samba share with:
```
gvfs-mount smb://server/share
```

It always fails with this message:
```
Error mounting location: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

The good news is when I use Nautilus to open one of the shares from a bookmark it works perfectly.

Anyone else noticed a change in gvfs-mount behaviour recently?

k

---

### Post by kamaji792 on 2011-12-09
Hmm...

I just noticed that when Nautilus mounts the Samba share the url is
```
smb://user-name@server/share
```

And so if I do the following at the command line:
```
gvfs-mount smb://user-name@server/share
```

It appears to mount without any problems.

Atb k

---

### Post by Morbius1 on 2011-12-09
There was a bug that I suspect would apply to both methods: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/463267)

Did you by any chance save a password for that remote share?

Maybe adding the username is another workaround.

---

### Post by kamaji792 on 2011-12-09
Hi Morbius1,

The shares do need a password, but I believe that that is handled by the keyring ting (you can tell I don't really understand this bit).

I've come across threads that talk about resetting the keyring password but it never helped me.  I certainly did not do it to get my latest fix to work.

I have found gvfs-mount to be a bit flaky.  Always worked better if did it just after booting the server.  Occasionally required repeat attempts to get it to mount the share.

I will update this thread if I get similar problems with it failing to mount shares but at the moment I am happy.

k

---

