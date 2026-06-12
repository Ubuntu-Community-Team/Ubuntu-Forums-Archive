---
title: "VMware Player"
date: 2010-04-11
forum: General Help
---

### Post by rjmach on 2010-04-11
Hello I need help with Ubuntu 9.10 in VMware Player.I have tried to load Nvidia driver.
This is what i have tried and dose not work. I could use help on this.):P


Ubuntu does not ship with NVIDIA 3D acceleration enabled. Getting the NVIDIA Geforce video card working to it's full potential requires the installation of an additional glx driver package. The nvidia-glx driver will allow us to make better use of the Geforce type video card. The process is simple, however many tutorials make it more complex than need be. The Process: Open a terminal and type sudo apt-get update Type sudo apt-get install nvidia-glx Type sudo apt-get upgrade Type sudo dpkg-reconfigure xserver-xorg Select the nvidia driver from the X server driver list and follow the on-screen steps to complete the configuration Once finished with the configuration, hold down Ctrl+Alt+Backspace to restart X server. You should be presented with a nice NVIDIA splash screen signaling that the driver is installed and working You can test this in the terminal by typing glxinfo | grep direct (the output should be direct rendering: yes) You can also type glxgears to watch your card at work Source is : [http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/)

---

### Post by rtilson on 2010-04-12
I have not been able to get 3D in VMware Player to work. One is that you cant install the nvidia driver in a virtual machine. Once you have installed the vm tools that 3D is supposed work.

I have been able to get 3D working using VirtualBox.

---

### Post by rjmach on 2010-04-12
> **rtilson said:**
> I have not been able to get 3D in VMware Player to work. One is that you cant install the nvidia driver in a virtual machine. Once you have installed the vm tools that 3D is supposed work.

I have been able to get 3D working using VirtualBox.

How did you get it to work in VirtualBox? I can try it in VB:popcorn:
If you can let me know how you did it! I am running Window7 :smile:

---

### Post by rtilson on 2010-04-12
Install Ubuntu in Virtualbox...then install the virtual machine tools...shutdown the virtual machine...in the VirtualBox settings make sure that that 3D acceleration is enables and that video memory is to the max it can go...restart virtual machine...when you login back in 3D should be working...if it is not you might have to enable it in the Appearance => Visual Effects tab.

To test open a terminal type glxinfo look for direct rendering = yes...if yes 3D is enabled

---

### Post by 3rdalbum on 2010-04-12
> **rjmach said:**
> Hello I need help with Ubuntu 9.10 in VMware Player.I have tried to load Nvidia driver.
This is what i have tried and dose not work. I could use help on this.):P

Two things. Firstly, although your "host" has an Nvidia card, the "guest operating system" does not. You can't have two operating systems accessing the graphics card at the same time. So don't install the Nvidia driver.

Secondly, the piece of information you linked to is for Ubuntu 6.10 running on real hardware. You're trying Ubuntu 9.10. The information is so old and outdated that there's no part of it that will work on current versions of Ubuntu! It's like finding a set of instructions for doing something in Windows 98, and attempting to follow them on Windows 7.

---

### Post by dcstar on 2010-04-13
> **3rdalbum said:**
> Two things. Firstly, although your "host" has an Nvidia card, the "guest operating system" does not. You can't have two operating systems accessing the graphics card at the same time. So don't install the Nvidia driver.

Secondly, the piece of information you linked to is for Ubuntu 6.10 running on real hardware. You're trying Ubuntu 9.10. The information is so old and outdated that there's no part of it that will work on current versions of Ubuntu! It's like finding a set of instructions for doing something in Windows 98, and attempting to follow them on Windows 7.

Thirdly, **all** VM issues should be posted in the VM forum.

---

