---
title: "Nvidia GTX 460 Drivers in 10.10 not working"
date: 2011-01-18
forum: General Help
---

### Post by charliehorse55 on 2011-01-18
I just upgraded to 10.10 from 10.04. I used to have a manual install of the nvidia drivers configured (by downloading binary from Nvidia website) but right before I upgraded I used nvidia-uninstall to remove it. Upon rebooting into 10.10 I went to Additional drivers and activated nvidia-current. After I rebooted I still had no driver, so I looked in the Additional Drivers pane again. It says Nvidia-current is activated but not currently in use. Then I went to a terminal and typed:

sudo nvidia-xconfig

Thinking it would reconfigure X to work with my 460, however it instead said:

command not found


What's going on here?

---

### Post by charliehorse55 on 2011-01-18
Please help! I have now tried deleting my xorg.conf and it didn't do anything! I am at a loss as to why the program "nvidia-xconfig" is not installed.

---

### Post by gmargo on 2011-01-18
nvidia-xconfig is part of the nvidia-current package.  If it is not in your $PATH then perhaps there was an installation problem since it depends on some symbolic links.

```

$ ls -l `which nvidia-xconfig`
lrwxrwxrwx 1 root root 32 Oct 22 19:59 /usr/bin/nvidia-xconfig -> /etc/alternatives/nvidia_xconfig
$ ls -l /etc/alternatives/nvidia_xconfig
lrwxrwxrwx 1 root root 42 Oct 22 19:59 /etc/alternatives/nvidia_xconfig -> /usr/lib/nvidia-current/bin/nvidia-xconfig

```I'm running the latest driver, installed from this ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by charliehorse55 on 2011-01-19
Thanks, I already tried removing and purging the package but upon re-install it was still non-functional. 

I installed the driver the manual way from the nvidia website and it's working perfectly, I just don't like how I have to recompile the kernel module every time I update my kernel (which is amplified by the fact that Ubuntu doesn't warn you about Kernel updates and just throws them in with the rest of the updates).

---

