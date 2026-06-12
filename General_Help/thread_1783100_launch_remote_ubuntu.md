---
title: "launch remote ubuntu"
date: 2011-06-15
forum: General Help
---

### Post by pacalici on 2011-06-15
hello,

i just installed ubuntu on a remote windows server, using wubi. now.. how can i launch ubuntu? restarting the remote machine obviously disconnects my session. is there some way to access the grub menu from windows?

thanks

---

### Post by christopher.adams360 on 2011-06-15
How are you connecting to your remote server?

If you are using VNC or Windows Remote Desktop, you are not going to be able to launch Ubuntu remotely.

---

### Post by pacalici on 2011-06-15
yes, i'm using windows remote desktop. definitely, no way?:-/

---

### Post by ruffEdgz on 2011-06-15
I don't think wubi is used to run both Ubuntu and Windows at the same time. 

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Just looking over some wubi documentation, it seems you can select which OS go to from the Windows Boot Manager: [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I select whether to run Windows or Ubuntu?

Did you make a VM of Ubuntu on that Windows Server?

EDIT: You might be able to look into changing the boot order for the Windows Boot Manager to point to Ubuntu instead of Windows but I don't know how to change it back to Windows if you wanted to go back: [http://blogs.technet.com/b/aralves/archive/2007/07/17/windows-server-2008-boot-manager.aspx](http://blogs.technet.com/b/aralves/archive/2007/07/17/windows-server-2008-boot-manager.aspx)

---

### Post by pacalici on 2011-06-15
i want to be able to switch between windows and ubuntu, settin ubuntu as the default os is not an option (and neither is cygwin). waitin for suggestions..

no, i didn't set an ubuntu virtual machine, just installed it using wubi, without givin' any thought to how i'd start it after the installation.


> **ruffEdgz said:**
> I don't think wubi is used to run both Ubuntu and Windows at the same time. 

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Just looking over some wubi documentation, it seems you can select which OS go to from the Windows Boot Manager: [https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I select whether to run Windows or Ubuntu?

Did you make a VM of Ubuntu on that Windows Server?

EDIT: You might be able to look into changing the boot order for the Windows Boot Manager to point to Ubuntu instead of Windows but I don't know how to change it back to Windows if you wanted to go back: [http://blogs.technet.com/b/aralves/archive/2007/07/17/windows-server-2008-boot-manager.aspx](http://blogs.technet.com/b/aralves/archive/2007/07/17/windows-server-2008-boot-manager.aspx)

---

### Post by Gregorybekkers on 2011-06-15
Change the grub config file?

---

### Post by ruffEdgz on 2011-06-15
> **pacalici said:**
> i want to be able to switch between windows and ubuntu, settin ubuntu as the default os is not an option (and neither is cygwin). waitin for suggestions..

no, i didn't set an ubuntu virtual machine, just installed it using wubi, without givin' any thought to how i'd start it after the installation.
Here is what I am getting from this post:
[LIST]
[*]Windows Server and Ubuntu installed using the same machine (used wubi)
[*]Does not want to change the default boot manager for Windows
[*]The Windows Server is not located near you
[*]Would like to switch between the two servers remotely
[/LIST]
Is that all right, did I leave anything out?

From my understanding, placing Ubuntu with a Windows server is easily done with wubi but to switch between the two, you need to change the default boot option or be at the machine to select which OS to use. If there is another way to complete this, I would be very interested in how this can be accomplished.

---

### Post by pacalici on 2011-06-15
as i often need to switch between windows and ubuntu, it seems tedious to keep changin the default boot operating system. but if that's the only way to do this..
[the machine is located in my building, but it's locked up, so it might as well be on mars.]

---

### Post by christopher.adams360 on 2011-06-15
The only way you will be able to do what you are asking is to run Ubuntu in a virtual machine.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

VirtualBox is virtual machine system that will enable you to run them at the same time.

I highly recommend you uninstall the Wubi version and install Ubuntu in a VM.  It will make switching between the two much, much simpler.

Like I said, using Remote Desktop, it will be very difficult to switch between the two, as it is not compatible with Ubuntu, but you won't have that problem using virtualization.

---

### Post by pacalici on 2011-06-16
thank you, christopher.adams360, i will try it out (and hopefully not come back for a follow-up).

have a sunny day


> **christopher.adams360 said:**
> The only way you will be able to do what you are asking is to run Ubuntu in a virtual machine.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

VirtualBox is virtual machine system that will enable you to run them at the same time.

I highly recommend you uninstall the Wubi version and install Ubuntu in a VM.  It will make switching between the two much, much simpler.

Like I said, using Remote Desktop, it will be very difficult to switch between the two, as it is not compatible with Ubuntu, but you won't have that problem using virtualization.

---

