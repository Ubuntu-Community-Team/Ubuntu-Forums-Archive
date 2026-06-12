---
title: "Virtual Box Windows XP installing problem"
date: 2011-02-10
forum: General Help
---

### Post by Baharmur on 2011-02-10
Hello,
I am trying to install Windows XP on my VirtualBox. I got an error message:

p, li { white-space: pre-wrap; } The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000FF]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I have the DKMS intsalled, but when i try to execute the command, i get this:

```
bahar@bahar:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                            *  done.
 * Uninstalling old VirtualBox DKMS kernel modules                              /etc/init.d/vboxdrv: 383: cannot create /var/log/vbox-install.log: Permission denied
 *  done.
 * Trying to register the VirtualBox kernel modules using DKMS                  /etc/init.d/vboxdrv: 383: cannot create /var/log/vbox-install.log: Permission denied

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        /etc/init.d/vboxdrv: 383: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
```

Do you have a solution for this problem?

---

### Post by Baharmur on 2011-02-10
I have solved the problem.
I had just forgotten to write "sudo", that was it:)

---

### Post by 3Miro on 2011-02-10
Usually you have to reboot right after you install Virtual Box or load the modules manually:

```
modprobe vboxdrv
modprobe vboxnetflt
modprobe vboxnetadp
```

If you have to run /etc/init.d/vboxdrv setup, then you should do it as "root"

```
sudo /etc/init.d/vboxdrv setup
```

You probably need to add yourself to the vboxusers group, goto System -> admin -> Users and Groups.

---

### Post by 3Miro on 2011-02-10
Please mark the thread as "solved".

---

