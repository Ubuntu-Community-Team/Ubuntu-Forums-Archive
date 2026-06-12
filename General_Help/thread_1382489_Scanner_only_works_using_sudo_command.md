---
title: "Scanner only works using sudo command"
date: 2010-01-16
forum: General Help
---

### Post by Gunnercw02 on 2010-01-16
Still new to Ubuntu and learning my way around. I've got a problem with my Brother MFC 5440cn all in-one printer that will only scan using the sudo command. It will work with Xsane or Skanlite using this command only but nothing else each program says no device found. When I run lsusb it does not show my printer but i can print from it. This has got me baffled?

bill@Bill-Desktop:~$ lsusb
Bus 001 Device 003: ID 13fe:3100 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
bill@Bill-Desktop:~$

Any help will be appreciated.

Thanks,
Bill

---

### Post by plucky on 2010-01-16
Have you installed "sane-utils".Open **Synaptic Package Manager** and search for sane-utils and install.

Also according to the [Brother Solution Center](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10) you have to add a couple of lines to "/lib/udev/rules.d/40-libsane.rules" file.


Good Luck

---

### Post by Gunnercw02 on 2010-01-16
Thanks i'll give that a shot, however editing command lines and config files i'm a real novice. Been working through the book but still trying to get my arms around it.

Thanks again.

---

### Post by Gunnercw02 on 2010-01-16
I already had sane-utils and the libsane already installed any other suggestions will be greatly appreciated.

Thanks for the help

---

