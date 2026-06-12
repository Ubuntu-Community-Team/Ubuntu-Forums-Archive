---
title: "Connect to Windows Share via terminal"
date: 2012-02-25
forum: General Help
---

### Post by Tropicalbound on 2012-02-25
Hello,

When I connect to a network share using the GUI, I can access it via Terminal by going to /home/mylogon/.gvfs.  Can anyone tell me how to initiate this connection using the Terminal and not going through the GUI first?

I did some research on mounting a drive to a Windows Share, but I'm afraid what I found was over my head.  Thanks for your patience!

TB

---

### Post by Morbius1 on 2012-02-25
```
gvfs-mount smb://server/share
```It will mount to /home/mylogon/.gvfs/share on server

"server" can be the host name or the ip address.

[COLOR=Blue]**EDIT**[/COLOR]: BTW to unmount this share:
```
 gvfs-mount -u smb://server/share
```

---

### Post by Tropicalbound on 2012-02-25
Thanks for the reply Morbius1.  When I run the command, it says gvfs is not found.  If I try apt-get install gvfs, it says it's already installed.

What am I missing?

TB

---

### Post by Tropicalbound on 2012-02-25
I put a space between gvfs and -mount.  It didn't like that.  All is good when I type the command just as you instructed.;)

That's exactly what I was looking for.  Thanks!!!

TB

---

### Post by baumanno on 2012-02-25
Tropicalbound,

I vaguely remember once needing the gvfs-backends to connect to a share, maybe

```
sudo apt-get install gvfs-backends
```

does the trick?

EDIT: fixed

---

