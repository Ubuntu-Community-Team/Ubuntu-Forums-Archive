---
title: "After upgrade there was no GUI"
date: 2010-12-18
forum: General Help
---

### Post by karthick87 on 2010-12-18
I am using ubuntu 10.10.After upgrade there was no GUI..How can i get into GUI??

My outputs:[B]
glxinfo | grep vendor[/B]
```
server glx vendor string: SGI 
 client glx vendor string: MesaProject and SGI 
 openGL vendor string: mesa project
```**lspci | grep VGA**
```
Intel corporation core processor integrated graphics controller (rev 02)
```

---

### Post by oldfred on 2010-12-18
Are you running the above commands from a command line? Or you have booted ok, just that you do not get the GUI.

Many are having video issues. You may need nomodeset, i915.modeset=0 or =1  or even the generic setting. Try rebooting and entering each setting as above.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

