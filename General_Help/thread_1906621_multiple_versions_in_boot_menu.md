---
title: "multiple versions in boot menu"
date: 2012-01-09
forum: General Help
---

### Post by phillyj on 2012-01-09
I have a dual boot with Lucid Lynx (Ubuntu 10.04 LTS). I have it set up so that each time I turn on the computer, I am asked if I want Ubuntu, recovery, or Windows 7. 

For the past few updates, I have noticed the list of Ubuntu choices increase. Currently there are versions labeled "Ubuntu Linux 2.6.32-3x-generic" where x=3,4,5,6,7. For each of these options, there is also a recovery option. So for Ubuntu choices, I have 10 options.

The problem is not that I have so many but that none of the options have functional wireless connectivity except for 2.6.32-33. What is going on? Do I have to reinstall my wireless driver each time I have a big update? Also, how do I make sure that only the latest update shows up in the boot menu? The way things are going, the boot menu is gonna be so big and annoying to use.

Thanks.

I am using an HP laptop, Pavilion DV6. I can't recall if I have the 32 or 64 bit. I think it is 64 bit version on the llano AMD chip

---

### Post by imachavel on 2012-01-09
uname -m
i686

x86 = 32 bit x64 = 64 bit

there you go:

[http://stackoverflow.com/questions/246007/how-to-determine-whether-a-given-linux-is-32-bit-or-64-bit](http://stackoverflow.com/questions/246007/how-to-determine-whether-a-given-linux-is-32-bit-or-64-bit)

as for several options in grub, it shouldn't effect your system too bad at all. But if more and more options keep popping up it could be a kernel loading error when the pc tries to read grub :confused:

---

### Post by Basher101 on 2012-01-09
this is the only thing that makes a mess on Ubuntu. It is intended to leave the older kernel version in case the newer one does not work, so you have a backup. I don't know about your wireless as it is, you should open a seperate thread for that one.

If you want to remove the other kernels you will need to use Synaptic package manager.

Once you opened it, type in the search box "linux-image" now you should get a list with kernels. On the left is a green square for those kernels you have currently installed. Simply rightclick all the kernels you want to remove and mark them for removal. Click the small arrow at the top to apply and it will start deleting (you will also free up alot of space, 1 Kernel is ~ 80 MB). To get rid of all the entries in grub you must update the list with the command ```
sudp uptdate-grub
``` and voliá! you uninstalled all unneeded kernels:popcorn:

regards

---

### Post by Paqman on 2012-01-09
> **Basher101 said:**
> To get rid of all the entries in grub you must update the list with the command ```
sudo update-grub
``` 

Uninstalling a kernel actually does this automatically. You might want to make sure you uninstall any headers you have, too.

---

### Post by phillyj on 2012-01-09
> **Basher101 said:**
> 
Once you opened it, type in the search box "linux-image" now you should get a list with kernels. On the left is a green square for those kernels you have currently installed. Simply rightclick all the kernels you want to remove and mark them for removal. Click the small arrow at the top to apply and it will start deleting (you will also free up alot of space, 1 Kernel is ~ 80 MB). To get rid of all the entries in grub you must update the list with the command ```
sudp uptdate-grub
``` and voliá! you uninstalled all unneeded kernels:popcorn:

regards

Ok, I see this. Whenever a new kernel is installed, should it be able to use drivers installed in a previous kernel? The wireless driver was a manual install using software from the manufacturer. I installed it into the 33 kernel but every other kernel I installed had a non functioning wireless so I only use the 33 kernel. 

The driver was a bit hard for me to install (being a noob) and so I'm hesitant to go do it again.

---

### Post by cortman on 2012-01-09
Each kernel is totally separate, so no, they don't utilize previous version's drivers.
You can also remove kernels simply by deleting them in /boot, although using Synaptic is probably a good idea.

---

