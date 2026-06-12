---
title: "Script for printing VirtualBox"
date: 2010-09-27
forum: General Help
---

### Post by obrer on 2010-09-27
Have lucid as main operating system and have installed windows in virtualbox, the problem I have is that when I use the USB printer in virtualbox, it disappears in Ubuntu, I now the commands for attaching and deattaching printer in virtualox “eg: VBoxManage controlvm Linux usbattach sysfs:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1//device:/dev/bus/usb/003/002”, what I would need is a script that would deatach de usb printer from virtualbox automatically when I print in ubuntu. 

Is this possible??

---

### Post by Jeroensum on 2010-09-27
Maybe it's easier not to let Windows access the printer directly but trough cups?

---

### Post by obrer on 2010-09-27
Yes, but I don't want windows to be connected to the network, unless I could only let connect windows to the lan network (I will look up this), no need internet nor want internet in windows, I only run 2 or 3 programs that are necessary for me and that only run on windows, but I don't want to set up a firewall, antivirus, spy-ware programs for these 3 programs that do not need internet, for security thats why I am in Linux and not in Windows.

---

