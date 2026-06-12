---
title: "X is toasted"
date: 2006-05-21
forum: General Help
---

### Post by kaydub on 2006-05-21
Hey all,

I'm hoping for a little help.  I've been using the ubuntu browser appliance for vmware for a while now.  All was well until a day ago when VM player choked as it shut down.

When I brought it back up, ubuntu starts, gdm tries to start, when X tries to start, it fails saying:

   X: cannot stat /etc/X11/X (no such file or directory) aborting

And it suggests I reconfigure X.

I'm not a complete newbie, but I can't figure out what broke or how to reconfigure X.  I've been trying all the troubleshooting as root under a console, so I shouldn't have any "sudo" type problems.

I tried the old "dpkg-reconfigure xserver-xorg" but that package is not installed.  What package should I specify to run the reconfigure?

Any ideas?

Thanks

---

### Post by Qrk on 2006-05-21
Easy fixes first, so try this. /etc/X11/X is a symlink, so you might just be missing it:

```
sudo ln -sf /usr/bin/Xorg /etc/X11/X
```

But if X really isn't installed, you may need to reinstall "ubuntu-desktop"

---

### Post by kaydub on 2006-05-22
Adding the sim link worked...

The weird thing is that I have another copy of this VM that works just fine but does not include this sim link.

Oh well, one of the config files must have gotten messed up somehow when VMware Player crashed.

Thanks for the help.

---

