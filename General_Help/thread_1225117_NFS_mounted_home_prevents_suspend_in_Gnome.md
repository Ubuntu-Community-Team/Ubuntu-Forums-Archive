---
title: "NFS mounted /home prevents suspend in Gnome"
date: 2009-07-28
forum: General Help
---

### Post by rothril on 2009-07-28
HELO

I have mounted my /home from a server over NFS. The relevant line
from the server's /etc/exports:

```
/home    desktop(rw)
```

The relevant line on the desktop's /etc/fstab:

```
server:/home    /home        nfs        rw,hard,intr      0
0
```

Both server and desktop are running a fully updated Jaunty.

Everything seems fine except suspending from Gnome. The screen goes
black with a flashing cursor and nothing more happens. And I have to
physically turn off the desktop It's possible to switch to a virtual
terminal but logging in just hangs. If I log out I can suspend from
GDM no problem. I can also log in at a VT and suspend with

```
sudo pm-suspend
```

Suspend from Gnome works great with a local /home.

I had a setup like this with Hardy and it worked fine. I didn't try it
in Intrepid. Could this be to do with the suspend improvements in
Jaunty? I would be grateful for any help in troubleshooting this. I'm
not sure what logs I should be looking at or what I should be looking
for. Should I try changing anything in my /etc/exports or /etc/fstab?
Should this be reported as a bug? If so, against what?

Thanks.

---

### Post by MountainX on 2011-01-07
I have this problem too (with Maverick, 10.10).

My original post is here:
[http://ubuntuforums.org/showthread.php?p=10328627#post10328627](http://ubuntuforums.org/showthread.php?p=10328627#post10328627)

In that post I list some related bug reports:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/506116](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/506116)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292698](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292698)

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/30594](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/30594)

---

### Post by MaxIBoy on 2011-01-07
I don't know how to fix it, but as a workaround you could try sshfs instead.

---

### Post by MountainX on 2011-01-07
> **MaxIBoy said:**
> I don't know how to fix it, but as a workaround you could try sshfs instead.

All of my important files are on the server. SSHFS is slower than NFS, so that would have a huge impact on my efficiency since it would affect everything I do on my computer.

---

