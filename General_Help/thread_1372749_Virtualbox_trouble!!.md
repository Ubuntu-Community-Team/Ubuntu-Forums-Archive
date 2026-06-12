---
title: "Virtualbox trouble!?!"
date: 2010-01-04
forum: General Help
---

### Post by DeMartini on 2010-01-04
I installed VB OSE onlt]y to learn that there is no usb support (spent hours going through posted workarounds to no avail!)My understanding is to have usb support you have to install the full binary version, i'm not sure how to do this correctly & it's frustrating installing VB & an OS just to keep finding out it's w/o usb support, any HELP would be really appreciated, thanks sooooo much:)

---

### Post by mkvnmtr on 2010-01-04
I have done it and I think it is a better product than the one in the repositories.Very simple to make the change. Open the package manager and type virtual box in the search box. Not the quick search. Then remove virtual box completely. Then go to the virtual box download site and download the package for linux. It will tell you that you need three other programs for it to work. When I searched my system they had been installed with the first box and were still there. When it is setting on your desktop just double click on it and the installer will take over. I seem to remember having to answer a question or two but that is all.when it is installed you can put the package you downloaded in the trash. Might have to restart to get it in the menu. I have support for usb. In fact I am installing my second distro now.

---

### Post by cybergalvez on 2010-01-04
get VB from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads), the version from sun has usb support

---

### Post by jamesisin on 2010-01-04
I was able to find a repo for VB and the necessary security key so I was able to add VB to Synaptic.  I would recommend that path for anyone.  I did a Google search just now and found one example:

[http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/](http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/)

That's a place to start.

---

### Post by DeMartini on 2010-01-04
> **mkvnmtr said:**
> I have done it and I think it is a better product than the one in the repositories.Very simple to make the change. Open the package manager and type virtual box in the search box. Not the quick search. Then remove virtual box completely. Then go to the virtual box download site and download the package for linux. It will tell you that you need three other programs for it to work. When I searched my system they had been installed with the first box and were still there. When it is setting on your desktop just double click on it and the installer will take over. I seem to remember having to answer a question or two but that is all.when it is installed you can put the package you downloaded in the trash. Might have to restart to get it in the menu. I have support for usb. In fact I am installing my second distro now.yeah followed your advice all went well i tried to load/start the new OS Win7 I get this error:
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

---

### Post by jamesisin on 2010-01-04
If you use the repo method I recommended Synaptic should be able to manage all dependency issues.

---

### Post by mkvnmtr on 2010-01-05
I found the DKMC package installed on my machine. I would say that you should get the repositories like the other poster advised. Then you will also want to add yourself to the vbusers group. You can do this in administration users and groups. On my install it was the last group listed. Do not enable root to use vbox.

---

### Post by mvalenti on 2010-01-05
I did this last night got windows xp up and running..

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Then I hosed it when I was installing drivers for synaptics touchpad...

---

### Post by DeMartini on 2010-01-05
Thanks so much for all the great advice, i'm about to give this another try!:guitar:

---

