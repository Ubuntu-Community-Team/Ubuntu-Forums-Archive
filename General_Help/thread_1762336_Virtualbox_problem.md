---
title: "Virtualbox problem"
date: 2011-05-19
forum: General Help
---

### Post by stevepetmonkey on 2011-05-19
Having trouble with Virtualbox.
Everytime I try to start a guest OS I get an error:

[FONT="Arial Black"]Failed to open a session for the virtual machine Windows7.
The virtual machine 'Windows7' has terminated unexpectedly during startup with exit code 1.

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/FONT]

When I try this it does not work, it says file not found and browsing to the location confirms indeed that the file does not exist, I did find another file there called [FONT="Arial Black"]vboxdrv.dpkg-dist[/FONT] and so I tried this command:

[FONT="Arial Black"]/etc/init.d/vboxdrv.dpkg-dist setup[/FONT]

This worked and I am able to run guest OS after running this command, everytime!! But it is a bit of a hassel and I cant let the kids mess with this when they want to get on windows to use itunes!

I'm not really sure how or why it works, was just a lucky trial and error, can anybody help me fix it permanantly???

(I am running Virtualbox 3.2.1 on Maverick, I found this is the only one I can get running.)

Cheers, Steve.

---

### Post by wildmanne39 on 2011-05-19
> **stevepetmonkey said:**
> Having trouble with Virtualbox.
Everytime I try to start a guest OS I get an error:

[FONT="Arial Black"]Failed to open a session for the virtual machine Windows7.
The virtual machine 'Windows7' has terminated unexpectedly during startup with exit code 1.

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/FONT]

When I try this it does not work, it says file not found and browsing to the location confirms indeed that the file does not exist, I did find another file there called [FONT="Arial Black"]vboxdrv.dpkg-dist[/FONT] and so I tried this command:

[FONT="Arial Black"]/etc/init.d/vboxdrv.dpkg-dist setup[/FONT]

This worked and I am able to run guest OS after running this command, everytime!! But it is a bit of a hassel and I cant let the kids mess with this when they want to get on windows to use itunes!

I'm not really sure how or why it works, was just a lucky trial and error, can anybody help me fix it permanantly???

(I am running Virtualbox 3.2.1 on Maverick, I found this is the only one I can get running.)

Cheers, Steve.

Hi, type sudo apt-get DKMS in terminal on the guest host not the guest and then you can run /etc/init.d/vboxdrv setup

---

### Post by wildmanne39 on 2011-05-19
> **stevepetmonkey said:**
> Having trouble with Virtualbox.
Everytime I try to start a guest OS I get an error:

[FONT="Arial Black"]Failed to open a session for the virtual machine Windows7.
The virtual machine 'Windows7' has terminated unexpectedly during startup with exit code 1.

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/FONT]

When I try this it does not work, it says file not found and browsing to the location confirms indeed that the file does not exist, I did find another file there called [FONT="Arial Black"]vboxdrv.dpkg-dist[/FONT] and so I tried this command:

[FONT="Arial Black"]/etc/init.d/vboxdrv.dpkg-dist setup[/FONT]

This worked and I am able to run guest OS after running this command, everytime!! But it is a bit of a hassel and I cant let the kids mess with this when they want to get on windows to use itunes!

I'm not really sure how or why it works, was just a lucky trial and error, can anybody help me fix it permanantly???

(I am running Virtualbox 3.2.1 on Maverick, I found this is the only one I can get running.)

Cheers, Steve.
The last command is also on the host system

---

### Post by stevepetmonkey on 2011-05-19
Tried that:

**E: Invalid operation DKMS**

---

### Post by rkillcrazy on 2011-05-19
> **stevepetmonkey said:**
> Tried that:

**E: Invalid operation DKMS**

```
sudo apt-get install dkms
```

I don't know if **dkms** is to be capitalized or not but you need to tell **apt-get** what to do.  In this case, **INSTALL**.

---

### Post by SeijiSensei on 2011-05-19
Did you add the VirtualBox repositories as described [here]("http://www.virtualbox.org/wiki/Linux_Downloads")?  If not, I **strongly** suggest removing your current VirtualBox installation, then adding the VB repository at Oracle as described in the part of the linked page that concerns "Debian-based distributions."  After following those instructions, install VirtualBox with "sudo apt-get install virtualbox-4.0".  

If you don't use the repository, you'll have persistent issues keeping the VB kernel module in sync with new kernel upgrades from Ubuntu.  You can install all the DKMS stuff so VB upgrades can compile a new kernel module, but it's a whole lot easier just to use the official repository at Oracle.

---

### Post by wildmanne39 on 2011-05-19
> **SeijiSensei said:**
> Did you add the VirtualBox repositories as described [here]("http://www.virtualbox.org/wiki/Linux_Downloads")?  If not, I **strongly** suggest removing your current VirtualBox installation, then adding the VB repository at Oracle as described in the part of the linked page that concerns "Debian-based distributions."  After following those instructions, install VirtualBox with "sudo apt-get install virtualbox-4.0".  

If you don't use the repository, you'll have persistent issues keeping the VB kernel module in sync with new kernel upgrades from Ubuntu.  You can install all the DKMS stuff so VB upgrades can compile a new kernel module, but it's a whole lot easier just to use the official repository at Oracle.
HI, does your method allow for usb to be working in the guest? I have been using vb for three years and as long as all the packages are installed I have never had any problem using the one from there site, people use to say that was the only way to get usb support.

---

### Post by SeijiSensei on 2011-05-19
> **wildmanne39 said:**
> HI, does your method allow for usb to be working in the guest?

You also need to install the proprietary "Extension Pack" as described on the [main downloads page]("http://www.virtualbox.org/wiki/Downloads").

---

### Post by linuxinstalledfromhdd on 2011-05-20
You are using an outdated version of Virtualbox..

Always use the latest software from the PPA instead:

Uninstall your current version of Virtualbox... in synaptic package manager. 

When you have gotten rid of it, now you can install the latest version of Virtualbox.

**Install VirtualBox 4 in Ubuntu – System Emulator**

 
 
 Add the VirtualBox repository and install the latest VirtualBox 4.0.6  in Ubuntu 11.04 Natty Narwhal, 10.10 Maverick Meerkat or 10.04 Lucid  Lynx using the commands below (before this, make sure you remove any  VirtualBox 3.x version you may have installed):
 sudo echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add - sudo apt-get update sudo apt-get install virtualbox-4.0

---

### Post by linuxinstalledfromhdd on 2011-05-20
[B]Install VirtualBox 4 in Ubuntu – System Emulator

Add the VirtualBox repository and install the latest VirtualBox 4.0.6 in Ubuntu 11.04 Natty Narwhal, 10.10 Maverick Meerkat or 10.04 Lucid Lynx using the commands below (before this, make sure you remove any VirtualBox 3.x version you may have installed):

sudo echo "deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install virtualbox-4.0
[/B]

---

### Post by linuxinstalledfromhdd on 2011-05-20
Actually just go to this web site instead:

[http://www.ubuntugeek.com/virtualbox-4-0-4-released-and-ubuntu-10-1010-049-10-installation-instructions-included.html](http://www.ubuntugeek.com/virtualbox-4-0-4-released-and-ubuntu-10-1010-049-10-installation-instructions-included.html)

---

