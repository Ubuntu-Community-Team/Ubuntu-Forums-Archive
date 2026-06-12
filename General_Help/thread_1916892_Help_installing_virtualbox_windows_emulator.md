---
title: "Help installing virtualbox windows emulator"
date: 2012-01-28
forum: General Help
---

### Post by pinbill on 2012-01-28
Hello, I am trying to use virtual box to run windows xp. I am currently using a dual boot win7 and ubuntu. I would like to switch all the way to ubuntu but would like to be able to stream netflix first. Ok, with the windows cd in when I hit start on virtual box I get this message.

 p, li { white-space: pre-wrap; }  Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


Then when I run the setup comand in a terminal I get this.


robertwgrodeska@johnny8:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                  /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong

Can anyone help me with this,

Thanks,

Bill

---

### Post by bodhi.zazen on 2012-01-29
run that as root

```
sudo /etc/init.d/vboxdrv setup
```

---

