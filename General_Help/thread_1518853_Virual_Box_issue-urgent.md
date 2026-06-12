---
title: "Virual Box issue-urgent"
date: 2010-06-27
forum: General Help
---

### Post by mohammed85 on 2010-06-27
Hi guys,

I am having serious problems with VirualBox after a while I am getting this message

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

**

I have run this command 

 sudo /etc/init.d/vboxdrv.dpkg-bak setup

and this is what I get

* Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong


and this is what is inside the log file

Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.2.6

------------------------------
Deleting module version: 3.2.6
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.2.6/source ->
                 /usr/src/vboxdrv-3.2.6

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.31-16-generic cannot be found at
/lib/modules/2.6.31-16-generic/build or /lib/modules/2.6.31-16-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.31-16-generic package.
Failed to install using DKMS, attempting to install without
Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

what should I do?

---

### Post by dino99 on 2010-06-27
why are you using kernel 31, its oldish, update/upgrade your system

then remove/purge virtualbox (into synaptic) and .virtalbox into /home

now you can reinstall virtualbox again

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by mohammed85 on 2010-06-27
sorry about this simple question how can I upgrade the kernel?

---

### Post by howefield on 2010-06-27
> **mohammed85 said:**
> or you could install the linux-headers-2.6.31-16-generic package.

Have you tried this ?

---

### Post by mohammed85 on 2010-06-27
yes and this is what I get

E: Couldn't find package linux-headers-2.6.31-16-generic

---

### Post by howefield on 2010-06-27
Try synaptic, the package is available

[http://packages.ubuntu.com/karmic/linux-headers-2.6.31-16-generic](http://packages.ubuntu.com/karmic/linux-headers-2.6.31-16-generic)

---

### Post by mohammed85 on 2010-06-27
this is what I get

Error: Dependency is not satisfiable: linux-headers-2.6.31-16

---

### Post by howefield on 2010-06-27
Were it not for the footie, I'd hang around and help you, but seeing as it is about to start... 

Might be quicker doing as dino99 suggests and doing a complete removal of Virtualbox, then install the new version.

I wouldn't purge  ~/.virtualbox though, as any .vdi files you have already created might vanish.

---

### Post by techunit on 2010-06-27
Well what version of Ubuntu are you running I assume it is supported? you may need to purge Virtualbox before it will start working again.

```
sudo aptitude purge virtualbox-3.2
```

```
sudo aptitude purge virtualbox-ose-qt
```

Only run one of these in the terminal based on how you got virtualbox. The First is if you installed it from the official website.

The second is if you installed virtualbox from the package manager.

---

### Post by techunit on 2010-06-27
Why wouldn't you purge it? Then reinstall it. I have had problems with virtualbox and this one sounds like an installation error that went unlooked.

---

### Post by mohammed85 on 2010-06-27
thanks howefield I do wish England to win today:)..


I have managed to run remove the virtual box and then when I installed it again it gives me the same error!

---

### Post by mohammed85 on 2010-06-27
hi guys.

how can I upgrade my kernel to the latest version?

---

### Post by b0b138 on 2010-06-27
look in synaptic for the headers.  search linux-headers   and see what comes up

after you've got that installed run ```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by mohammed85 on 2010-06-28
hello...

that header is not in the Sypa? anything else?

---

### Post by dcstar on 2010-06-28
> **mohammed85 said:**
> hello...

that header is not in the Sypa? anything else?

Ask in the Virtualization forum where **all** the VM info is.

---

### Post by mohammed85 on 2010-07-02
Hi Guys,

I have managed to solve the issue by upgrading my kernel to 2.6.32-020632-generic

---

