---
title: "autofs, symbolic links at / root"
date: 2009-08-05
forum: General Help
---

### Post by washakie on 2009-08-05
Hello,

I've set up autofs with sshfs. This is a terrific solution for those who haven't done it yet, it is simple. Follow one of the numerous tutorials with whichever flavor of options suits your style. See here:
[http://www.google.com/search?q=autofs+sshfs+tutorial](http://www.google.com/search?q=autofs+sshfs+tutorial)

Now, to the questions.

1) I can't seem to figure out how to make the automounts be at the root level:

/automount1
/automount2
...

I tried:
$cat /etc/auto.master
```
/ file:/etc/auto.test --timeout=80
```
$cat /etc/auto.test
```
automount1 -fstype=fuse,nodev,allow_other,default_permissions,workaround=nodelaysrv,uid=1000,gid=1000,reconnect,umask=002,sshfs_debug,IdentityFile=/home/me/.ssh/id_rsa :sshfs\#me@myserver\:/remotedir_to_mount
```

This doesn't seem to work. I have to have my mount point prefixed by something (/mnt) for some reason. Is there a way around this?

2) I have symbolic links at the root level to my automounts, but they seem to keep the mounts active, even if I'm not calling them. Is there an option, or something I can use when I set up the symlink so this doesn't happen. NOTE: the symlinks are to directories a few 'into' the automount directory. 

Thanks!

---

### Post by jacobwg on 2012-05-13
This is an old thread, but I found it via Google and perhaps my solution might benefit others.

What I did was setup the autofs mount to a folder /mnt/folder and then symlink the share folder to /folder

Basically, after mounting the share under /mnt/folder, I did:

```

ln -s /mnt/folder /folder

``` 

Works well for me.

---

