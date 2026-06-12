---
title: "DKMS tree already contains: nouveau-0.0.15+git20090823"
date: 2010-02-20
forum: General Help
---

### Post by psykotrol on 2010-02-20
so I recently messed up by cancelling the installation of xserver-xorg-video-nouveau, and now when I try to uninstall, reinstall, or fix it, I get errors and permission denied (even as root)

when I run
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

it returns

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xserver-xorg-video-nouveau is not installed, so not removed
0 upgraded, 0 newly installed, 0 to removed and 0 not upgraded.
1 not fuly installed or removed.
After this operation, 0B of addition disk space will be used.
Setting up nouveau-kernel-source (0.0.15+git20090823) ...
Adding Module to DKMS build system

Error! DKMS tree already contains: nouveau-0.0.15+git20090823
You cannot add the same module/version combo more than once.
dpkg: error processing nouveau-kernel-source (--configure):
 subprocess installed post-installatin script returned error exit status 3
Error were encountered while processing:
 nouveau-kernel-sourcce
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I try to chmod -Rv the nouveau directory in /var/lib/dkms, I get permission denied for the following folders:
drivers
include
nouveau
patches


how do I force the uninstallation of nouveau so I can reinstall it? I already tried sudo apt-get install -f, and it didnt work

I also rm -rf'd the nouveau directory, then tried to reinstall it, but it still didnt work

what did I do wrong, and how can I fix it?

---

### Post by elitenoobboy on 2010-02-21
I also seem to be having problems with dkms tree stuff already being installed. Anybody know how to reset it?

```
Setting up nvidia-190-kernel-source (190.53-0ubuntu1~karmic~nvidiavdpauppa10) ...
Removing old nvidia-190.53 DKMS files...
/usr/sbin/dkms: line 107: /dev/fd/62: No such file or directory
Loading new nvidia-190.53 DKMS files...

Error! DKMS tree already contains: nvidia-190.53
You cannot add the same module/version combo more than once.
dpkg: error processing nvidia-190-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 3
```

---

### Post by raym0nd on 2010-02-23
> **elitenoobboy said:**
> I also seem to be having problems with dkms tree stuff already being installed. Anybody know how to reset it?


Error! DKMS tree already contains: nvidia-190.53
You cannot add the same module/version combo more than once.
dpkg: error processing nvidia-190-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 3[/code]

Try this. It worked for me:
$ sudo aptitude purge dkms
$ sudo aptitude install xserver-xorg-video-nouveau # The second command will reinstall dkms as well.

---

### Post by geoff123 on 2010-02-25
remove the nouveau-kernel-source

---

