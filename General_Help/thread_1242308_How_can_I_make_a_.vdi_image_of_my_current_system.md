---
title: "How can I make a .vdi image of my current system?"
date: 2009-08-17
forum: General Help
---

### Post by chris1950 on 2009-08-17
I want to make a copy of my current laptop as a .vdi so I can put it in a virtual machine for testing software and  config changes before actually adding it to my system.

---

### Post by ibuclaw on 2009-08-17
Only way I know is via VMWare: [http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

I /think/ VirtualBox can use VMWare images.

Regards
Iain

---

### Post by chris1950 on 2009-08-17
I don't have VMware is it free? Is there a program similar to Ghost, it could do it? Could I install Ghost in Wine and do it from there?

---

### Post by chris1950 on 2009-08-17
Thnx [[COLOR=#D40000]**tinivole**[/COLOR]]("http://ubuntuforums.org/member.php?u=490875")

Am downloading [SIZE=1]VMware vCenter Converter Standalone now. Its a tar.gz file. I never have done these before can I get a step by step from someone?
[/SIZE]

---

### Post by chris1950 on 2009-08-17
Got it DL'd and installed now can not find it in menu's to get it started.

---

### Post by ibuclaw on 2009-08-17
> **chris1950 said:**
> Got it DL'd and installed now can not find it in menu's to get it started.

Actually, I've just had a hard search around, and it appears that you can only use the Linux version on an ESX Server. :(

Scrap that:
```

sudo vmware-uninstall-converter.pl
sudo rm -r /var/log/vmware-vcenter-converter-standalone

```

And use remastersys instead:
```
gksudo gedit /etc/apt/sources.list
```
And put at the bottom:
```
# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```
Save and Exit, then run:
```
sudo apt-get update && sudo apt-get install remastersys
```

Then to create an ISO image of your Desktop:
```
sudo remastersys dist
```
Then copy it over to your home
```
cp /home/remastersys/remastersys/customdist.iso ~/my-system-backup.iso
```

Then start VirtualBox and create a new VM with the default settings for "Ubuntu", and add the newly created ISO to the Virtual CDROM drive.
Boot the VM and install.

If the VM boots, install it and there you go, you pretty much have a snapshot of your OS right there.

To clean the remastersys cache
```
sudo remastersys clean
```

More info here: [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Regards
Iain

---

### Post by chris1950 on 2009-08-17
Thanks

That cleared up my headache ](*,) - going nuts trying to get it to work. Will follow your instructions later when have more time. By the way I bookmarked this page and the link page.:)

---

### Post by Bram77 on 2009-08-28
I've installed the program on one of the Ubuntu 9.04 servers I'm maintaining. When I ran "sudo remastersys dist" it started installing ubuntu-desktop and a lot more without askin permission or anything... If I'd want a window manager installed I would have installed it already.... I sure hope it does what I hope it does, otherwise this is going to be a huge waste of time... (have to clean up the server).

---

### Post by P4man on 2009-08-28
Why would you need remastersys for this? (not a rethorical question, actual question). 

FWIW, I googled around and found this:
[http://forums.virtualbox.org/viewtopic.php?f=1&t=15177](http://forums.virtualbox.org/viewtopic.php?f=1&t=15177)

Havent tried it yet, but here is an interesting quote:

> You can use imaging software like CloneZilla to make a full disk backup of the OS you want to convert to a VM, then restore that image in the VM with the same application.

---

