---
title: "[SOLVED] problem updtaing Virtual Box../again"
date: 2012-01-22
forum: General Help
---

### Post by qwertyjjj on 2012-01-22
I just updated VB and now I get this error:

```

/etc/init.d/vboxdrv setup
WARNING: All config files need .conf: /etc/modprobe.d/i8k, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                  /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
jason@Inspiron-9300:~$ /etc/init.d/vboxdrv setup
WARNING: All config files need .conf: /etc/modprobe.d/i8k, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                  /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
jason@Inspiron-9300:~$ 

```

Any ideas what to do?
I have no idea how they do their updates but everytime I update VB, I get something go wrong.

---

