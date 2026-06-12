---
title: "Booting..."
date: 2010-01-15
forum: General Help
---

### Post by Dracar on 2010-01-15
Sorry for the following block of text: 

Not sure how to explain so I'll jump right in, in 2 weeks i have to install windows for a class I'm taking, i've got a partition on my first HDD for this, i also have a partition on it for ubuntu, and one for storage. Windows 7 is installed on another HDD, and has its own partition there. Because I am going to be moving the drive with ubuntu 2 times a week, and I won't always have it,I want to leave my boot intact, and have my windows 7 boot menu show ubuntu as a choice, which then shows grub or w/e. grub is intact atm, but to get to ubuntu I have to reboot and unplug all my other drives, this gets old.

Neither OS knows of the other, i installed windows first, a month or 2 ago, then to make sure i didn't interfere with my main drive i unplugged it for the install of ubuntu. 

i assumed it would be as simple as opening a boot.ini file, copying the windows entry, and changing the hard drive to 0,2 but I've learned that windows 7 doesn't have such a file, any ideas? And thanks a million in advanced for anything at all lol

---

### Post by Lars Noodén on 2010-01-15
You'll want to look at the bootloader, **grub**.  That must point to the other systems and will give you a choice at start up about which one to use.  

The reason that you have to install Windows first is that it looks for and messes up other systems.  This is an [old, intentional problem](http://www.birdhouse.org/beos/byte/30-bootloader/).  It keeps the OEMs from installing another OS first and then Windows afterwards.  Licensing prevents OEMs from installing Windows first and then using the windows tools to install another OS afterwards.  Voila.  Lock-in.

Another option would be to put the outdated systems in a virtual machine.  There is rarely a good use-case for virtualization, but experimentation is one of them.  Be warned that the performance will be lower.  [VirtualBox](http://www.virtualbox.org/) and [Qemu-kvm](http://www.ubuntugeek.com/qemu-machine-emulator-and-virtualizer-setup-in-ubuntu.html) are two convenient ones and would reduce the chances that Windows could soil the filesystems or bootloader.  They would also allow to keep **snapshots** so you could roll back in an instant to an earlier configuration, such as a fresh install.  [plain kvm](https://help.ubuntu.com/community/KVM/Directly) is also an option.  So you could install in the VM, then make a snapshot of the fresh install and then any time you need to 'reinstall', just go back to the snapshot.  After a particular arduous application installation is another good time to take a snapshot.

---

