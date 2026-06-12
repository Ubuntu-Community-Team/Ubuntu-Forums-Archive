---
title: "Question about Virtualbox Guest Additions"
date: 2010-07-07
forum: General Help
---

### Post by GuiGuy on 2010-07-07
I am running VB non-free, not the OSE version, as described at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) - the current version is 3.2.6

When I start a VB session, I get a message telling me that I am using guest additions 3.1 and should upgrade to 3.2.6. However, only the OSE guest additions appear in the repository. If I attempt to install it, Virtualbox is removed and replaced with the OSE version, at which point installed VB OSs no longer work. 

Does anyone know where I can get the 3.2.6 guest additions that works with VB non-OSE?

TIA

---

### Post by giddyup306 on 2010-07-07
> **GuiGuy said:**
> I am running VB non-free, not the OSE version, as described at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) - the current version is 3.2.6

When I start a VB session, I get a message telling me that I am using guest additions 3.1 and should upgrade to 3.2.6. However, only the OSE guest additions appear in the repository. If I attempt to install it, Virtualbox is removed and replaced with the OSE version, at which point installed VB OSs no longer work. 

Does anyone know where I can get the 3.2.6 guest additions that works with VB non-OSE?

TIA


I'm facing a similar issue.  When I upgraded to Lucid it gave me some BS about having to recompile the kernel.  After doing so it had switched it to the non PUEL version, so now nothing (like USB) worked. I don't remember what I did to get it back... now it says that I am using a version that is not suitable for production use.  I basically just ignore the warnings, because if I upgrade, I will probably have to reconfig everything.  Hopefully your and my issues are similar, because this is quite annoying. The message tells me to upgrade to 3.2.6 (like you did).  Good thing I just learned to ignore the messages.

Sorry for hijacking your thread, but I hope there is a common solution for both issues. ;)

---

### Post by Leppie on 2010-07-07
you have to remove the guest addons from within the guest os.
after this you can install the new version using the menu on top of of virtualbox.
go to Devices>Install Guest Additions...

---

### Post by GuiGuy on 2010-07-07
> **Leppie said:**
> you have to remove the guest addons from within the guest os.
after this you can install the new version using the menu on top of of virtualbox.
go to Devices>Install Guest Additions...

That's what I thought. But HOST + D (Install Guest Additions) does nothing. 

Any ideas?

Thanks

---

### Post by GuiGuy on 2010-07-08
> **giddyup306 said:**
>  The message tells me to upgrade to 3.2.6 (like you did).  Good thing I just learned to ignore the messages.


I have the 3.1.x iso file for the guest additions and other than the warnings it seem to work ok. 

Guess I'll leave it as that. 

Cheers

---

### Post by jocko on 2010-07-08
First unmount any cd you have attached to the guest os, then select "install guest additions" from the menu. That should mount the guest additions iso in the guest. If the guest is windows the install should start automatically.
If the guest is linux, you need to run the installer from the cd yourself. This should work:
```
cd /media/VBOXADDITIONS_3.2.6_63112
sudo ./autorun.sh
```

---

### Post by GuiGuy on 2010-07-08
> **jocko said:**
> First unmount any cd you have attached to the guest os, then select "install guest additions" from the menu. That should mount the guest additions iso in the guest. If the guest is windows the install should start automatically.
If the guest is linux, you need to run the installer from the cd yourself. This should work:
```
cd /media/VBOXADDITIONS_3.2.6_63112
sudo ./autorun.sh
```

There's my problem. Where do I get /media/VBOXADDITIONS_3.2.6_63112

If I unmount the current additions (host linux/ guest winXP), "install guest additions" does nothing.  

Thanks

---

### Post by Leppie on 2010-07-08
> **GuiGuy said:**
> There's my problem. Where do I get /media/VBOXADDITIONS_3.2.6_63112

If I unmount the current additions (host linux/ guest winXP), "install guest additions" does nothing.  
after unmounting the guest additions, you have to remove them (uninstall) from the guest os.

---

### Post by GuiGuy on 2010-07-08
> **Leppie said:**
> after unmounting the guest additions, you have to remove them (uninstall) from the guest os.

As pointed out above, that doesn't happen. If I uninstall, remove etc the earlier version and then click the "Install Guest Additions" menu item nothing happens.

---

### Post by endotherm on 2010-07-08
one thing I;ve noticed about VB that may help, is that it will sometimes keep mounted a copy of the old tools iso. I edit the machine to remove the old iso from the library, and leave the drive empty. then on reboot, I tell vb to install guest additions. this mounts the new iso, but since it is mounted as root, the autorun doesn;t pop up a window, so I do a quick 'ls -l /media' to see what the mount point is, and install it from the cli. 
here is how I ran it last:
```

Lucid:~$ cd /media
Lucid:/media$ ls
cdrom0  floppy  floppy0  VBOXADDITIONS_3.2.4_62467
Lucid:/media$ cd VBOXADDITIONS_3.2.4_62467/
Lucid:/media/VBOXADDITIONS_3.2.4_62467$ ls
32Bit        VBoxLinuxAdditions-amd64.run    VBoxWindowsAdditions.exe
64Bit        VBoxLinuxAdditions-x86.run      VBoxWindowsAdditions-x86.exe
AUTORUN.INF  VBoxSolarisAdditions.pkg
autorun.sh   VBoxWindowsAdditions-amd64.exe
Lucid:/media/VBOXADDITIONS_3.2.4_62467$ sudo sh ./VBoxLinuxAdditions-x86.run 

...

```

---

### Post by GuiGuy on 2010-07-08
> **endotherm said:**
> one thing I;ve noticed about VB that may help, is that it will sometimes keep mounted a copy of the old tools iso. I edit the machine to remove the old iso from the library, and leave the drive empty. then on reboot,

Excuse my obtuseness, but are the guest extensions distributed with VirtualBox PULE 3.2.x or do I have to download them separately?

I ask because I can totally uninstall, unmount, DELETE the 3.1 version, which I have as a separate file. Then when I click INSTALL GUEST ADDITIONS nothing happens.

To put my question another way, where is the Guest Additions 3.2.x file supposed to be when the user click "Install Guest Additions"?

Thanks for your patience.

Cheers

---

### Post by Leppie on 2010-07-09
> **GuiGuy said:**
> Excuse my obtuseness, but are the guest extensions distributed with VirtualBox PULE 3.2.x or do I have to download them separately?

I ask because I can totally uninstall, unmount, DELETE the 3.1 version, which I have as a separate file. Then when I click INSTALL GUEST ADDITIONS nothing happens.

To put my question another way, where is the Guest Additions 3.2.x file supposed to be when the user click "Install Guest Additions"?
the Guest Additions come with the 3.2.x PUEL edition.
what you could try is removing the version you've got installed now, and add the virtualbox repo and re-install from the repo.

---

### Post by GuiGuy on 2010-07-09
> **Leppie said:**
> the Guest Additions come with the 3.2.x PUEL edition.
what you could try is removing the version you've got installed now, and add the virtualbox repo and re-install from the repo.

I am installing from the repo. 

Thanks

---

### Post by Leppie on 2010-07-09
> **GuiGuy said:**
> I am installing from the repo. 

Thanks
let us know if it works ;)

---

### Post by GuiGuy on 2010-07-09
> **Leppie said:**
> let us know if it works ;)

Sorry, I meant that the install that is giving me problems was installed from the repo. 

The earlier version of the guest additions (3.1.x) was in /home/<user>/.VirtualBox - I removed it and tried again. No luck. "Install Guest Additions" doesn't do a thing.

I've reverted to 3.1 Guest Additions. I'll just have to put up with the warning it gives when I load the Guest OS. Other than that it seems to work anyway.

Thanks

---

### Post by jocko on 2010-07-10
The guest additions can be found in /usr/share/virtualbox/VBoxGuestAdditions.iso.
If it's not listed under CD/DVD images in the virtual media manager in virtualbox, just add it manually.

---

### Post by GuiGuy on 2010-07-10
> **jocko said:**
> The guest additions can be found in /usr/share/virtualbox/VBoxGuestAdditions.iso.
If it's not listed under CD/DVD images in the virtual media manager in virtualbox, just add it manually.

Many thanks. That's what I was looking for. All good.

For anyone else confronted with the issue I had, i.e. the "Install Guest Additions" menu item proved useless,

1) before starting the guest OS in VB, add /usr/share/virtualbox/VBoxGuestAdditions.iso to the STORAGE section in VirtualBox's GUI. 

2) Start your guest OS

3) Mount VBoxGuestAdditions.iso if it doesn't show up correctly

4) For Linux guest OS, open the mounted VBoxGuestAdditions.iso, then run autorun.sh. In Windows run the .exe

That's it. Worked me. 

Cheers

---

