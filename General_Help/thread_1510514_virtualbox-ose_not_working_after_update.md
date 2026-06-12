---
title: "virtualbox-ose not working after update"
date: 2010-06-15
forum: General Help
---

### Post by ismooth on 2010-06-15
recently i updated to a kernel version 2.6.31-22-generic and now I cannot start my virtual machines from virtualbox-ose.
when i try to run virtualbox modules i get this:

```
sudo /etc/init.d/virtualbox-ose start
 * Starting VirtualBox kernel modules
 * No suitable module for running kernel found                                      [fail]

```any ideas?

---

### Post by ju2wheels on 2010-06-16
You need to recompile the kernel modules after each upgrade to a new kernel.

Try running:

```

sudo /etc/init.d/virtualbox-ose setup

```

or this if that does not work (im running the closed source version so I dont know which will work):

```

sudo /etc/init.d/vboxdrv setup

```

Should then work on next reboot or start the vbox process manually as you attempted before.

---

### Post by ismooth on 2010-06-22
I tried running it but gives me only the usage:

```
Usage: /etc/init.d/virtualbox-ose {start|stop|stop_vms|restart|force-reload|status}

```There is no setup option.

---

### Post by ju2wheels on 2010-06-22
```

sudo apt-get --reinstall virtualbox-ose virtualbox-ose-dkms

```

This will not affect your VM's and installing dkms will make sure this is done automatically the next time you upgrade your kernel.

See if that helps.

---

