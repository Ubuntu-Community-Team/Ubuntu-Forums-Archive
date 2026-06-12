---
title: "NVidia broken because missing kernel source?"
date: 2012-03-31
forum: General Help
---

### Post by mrashley on 2012-03-31
Okay, so I updated my kernel twice before rebooting.

When I did I got a message from graphical X.

[INDENT]Ubuntu is running in low-graphics mode

The following error was encountered. You may ned to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages. Failed to load module "nvidia" (module-specific error, 0) No driver available.
[/INDENT]

So I tried ```
modprobe nvidia
``` and got 

[INDENT]FATAL: Module nvidia not found.[/INDENT]

So I tried rebooting to an older kernel 2.6.32-38 which had worked in the past. Same initial error.

So I tried ```
apt-get purge nvidia*
``` and reinstalled the nvidia-current package. I noticed a funny error, which I replicated by typing ```
sudo dpkg-reconfigure nvidia-current
```

The error:
[INDENT]Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed.[/INDENT]

So I ```
apt-get install kernel-source
``` and I get

Package kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-source has no installation candidate

So I've removed all "other" apt-get sources, and updated. Still the same issue. 

What am I doing wrong?

---

### Post by afrodeity on 2012-05-08
> **mrashley said:**
> Okay, so I updated my kernel twice before rebooting.

When I did I got a message from graphical X.

[INDENT]Ubuntu is running in low-graphics mode

The following error was encountered. You may ned to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages. Failed to load module "nvidia" (module-specific error, 0) No driver available.
[/INDENT]

So I tried ```
modprobe nvidia
``` and got 

[INDENT]FATAL: Module nvidia not found.[/INDENT]

So I tried rebooting to an older kernel 2.6.32-38 which had worked in the past. Same initial error.

So I tried ```
apt-get purge nvidia*
``` and reinstalled the nvidia-current package. I noticed a funny error, which I replicated by typing ```
sudo dpkg-reconfigure nvidia-current
```

The error:
[INDENT]Module build for the currently running kernel was skipped since the kernel source for this kernel does not seem to be installed.[/INDENT]

So I ```
apt-get install kernel-source
``` and I get

Package kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-source has no installation candidate

So I've removed all "other" apt-get sources, and updated. Still the same issue. 

What am I doing wrong?

Have same issue after pae kernel was installed, and manual installation of NVIDIA driver failed. There is supposed to be a kernel source in the repository, had this problem once I think it relates to kernel being out of sink with the release or something.

---

### Post by afrodeity on 2012-05-08
[http://ubuntuforums.org/showthread.php?t=1424275](http://ubuntuforums.org/showthread.php?t=1424275)

[http://www.nvnews.net/vbulletin/showpost.php?p=2164440&postcount=20](http://www.nvnews.net/vbulletin/showpost.php?p=2164440&postcount=20)

---

