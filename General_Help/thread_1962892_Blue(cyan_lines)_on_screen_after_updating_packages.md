---
title: "Blue(cyan lines) on screen after updating packages"
date: 2012-04-21
forum: General Help
---

### Post by Pithikos on 2012-04-21
I ran an update yesterday and nvidia got upgraded. Now I see cyan horizontal lines down the whole screen.

```

manos@megistanas:/var/log$ cat apt/term.log | grep nvidia
Preparing to replace nvidia-173 173.14.30-0ubuntu8 (using .../nvidia-173_173.14.30-0ubuntu8.1_amd64.deb) ...
Unpacking replacement nvidia-173 ...
Setting up nvidia-173 (173.14.30-0ubuntu8.1) ...
Loading new nvidia-173-173.14.30 DKMS files...
nvidia_173:
```What is the difference between nvidia-173 173.14.30-0ubuntu8 and 173.14.30-0ubuntu8.1? How can I rollback?

---

### Post by strafe_sawdoffe on 2012-04-21
Per this: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173)

... 8.1 it's definitely a security update. It might be easier to uninstall and reinstall the same version. If you need to rollback, the .deb files for version 8.0 are also available at that link. 

Possibly a better way to rollback is to use Synaptic Package Manager... you may need to install it, I think it was removed from later Ubuntu versions. Once it's installed, lanch it, and search for nvidia. It will find the 8.1 version. From there, you can highlight it, press "Package" on the menu bar, go to "Force Version," and force 8 to install instead of the latest.

---

