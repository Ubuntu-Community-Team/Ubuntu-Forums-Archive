---
title: "virtual box ose"
date: 2009-08-23
forum: General Help
---

### Post by tswoodii on 2009-08-23
i installed it successfully, created a virtual machine, and still cant get windows xp into the virtual machine. thought i did everything right. been reading the 200 something page manual...no help! confused, frustrated, stumped. can anyone help me?

---

### Post by blueridgedog on 2009-08-23
Are you using an XP install disk or an ISO of an XP install disk?

---

### Post by NickCollide on 2009-08-24
> **blueridgedog said:**
> Are you using an XP install disk or an ISO of an XP install disk?

Should that matter? I did it w/ an iso image - worked just fine (sans the ability to install the service packs or upgrade) ;)

NC

---

### Post by blueridgedog on 2009-08-24
> **NickCollide said:**
> Should that matter? I did it w/ an iso image - worked just fine (sans the ability to install the service packs or upgrade) ;)

NC

No, it doesn't matter, but it would change the way I tried to troubleshoot what was not working.

---

### Post by P4man on 2009-08-24
> **tswoodii said:**
> i installed it successfully, created a virtual machine, and still cant get windows xp into the virtual machine. thought i did everything right. been reading the 200 something page manual...no help! confused, frustrated, stumped. can anyone help me?

its not that hard really.. Did you configure your VM to boot from a windows install cd ? In virtualbox, select your vm, then settings, then CD/DVDROM.

Select "Mount a cdrom", and either select your (physical) cdrom drive there and insert a windows install cd, or select an image if you have a windows ISO file.

Then start the vm. 

If its not working, let us know whats happening.

---

### Post by 3rdalbum on 2009-08-24
> **tswoodii said:**
> i installed it successfully, created a virtual machine, and still cant get windows xp into the virtual machine. thought i did everything right. been reading the 200 something page manual...no help! confused, frustrated, stumped. can anyone help me?

What point are you at? For instance, have you changed the Virtualbox BIOS setting to boot from the Windows XP install CD? Are you up to that point yet? What's the last thing you can do before it fails, and how does it fail?

---

### Post by abhilash82 on 2009-08-24
I have done a complete Windows XP installation using Virtual Box and I did it from a CD.

If you are installing from the CD, go to the settings of the windows xp profile you have created in virtual box and click on CD/DVD drives.

Here you can mount a specific CD/DVD drive (using the drive letter) or you can add an ISO file which will get mounted.

When you start your session, based on the boot-up sequence, the CD or the image file will be invoked.

---

### Post by muteXe on 2009-08-24
How much space have you given your VM?

---

### Post by tswoodii on 2009-08-24
> **P4man said:**
> its not that hard really.. Did you configure your VM to boot from a windows install cd ? In virtualbox, select your vm, then settings, then CD/DVDROM.

Select "Mount a cdrom", and either select your (physical) cdrom drive there and insert a windows install cd, or select an image if you have a windows ISO file.

Then start the vm. 

If its not working, let us know whats happening.


this is all word for word of the two pop-up error boxes that appeared after attempting to start my vm.


first one;
VirtualBox-Error
Failed to open a session for the virtual machine windows xp pro.

Virtual Machine 'windows xp pro' has terminated unexpectedly during startup.

Details
Result code: Ns_ERROR_FAILURE
(0x80004005)
Component: Machine
Interface: IMachine
{540dcfda-3df2-49c6-88fa-033a28c2ff85}

second one;
VirtualBox-Error In suplibOs Init
Kernal driver not installed (rc=1908)

The VirtualBox Linux kernal driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernal module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora Or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles vboxdrv module if necessary.

and i do have the DKMS package installed.

---

### Post by tswoodii on 2009-08-24
that cool smiley is really supposed to be the number '8' followed by ')'
dont know why it did that

---

### Post by P4man on 2009-08-24
> The VirtualBox Linux kernal driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernal module by executing

'**/etc/init.d/vboxdrv setup**'.

Did you try running that ? 

```
sudo /etc/init.d/vboxdrv setup
```

Also there should be a user group called vboxusers and you should be a member of that. I think nowadays, vbox does that automatically during install, but check nonetheless in system > administration > users and groups. Unlock it, click usergroups and check there is one called vboxusers, and check you are a member of that group.

---

### Post by tswoodii on 2009-08-24
> **P4man said:**
> Did you try running that ? 

```
sudo /etc/init.d/vboxdrv setup
```Also there should be a user group called vboxusers and you should be a member of that. I think nowadays, vbox does that automatically during install, but check nonetheless in system > administration > users and groups. Unlock it, click usergroups and check there is one called vboxusers, and check you are a member of that group.

found vboxusers, but it was greyed out. couldnt click on it or do anything with it. now to run that command i use a terminal right? thats what i tried anyway.

---

### Post by P4man on 2009-08-25
> **tswoodii said:**
> found vboxusers, but it was greyed out. couldnt click on it or do anything with it.

You have to click "unlock" first, and give your password.

>  now to run that command i use a terminal right? thats what i tried anyway.

Yes; in a terminal.It would help if you posted the output here so we can see what happens when you run it..

---

### Post by abhilash82 on 2009-08-25
> **muteXe said:**
> How much space have you given your VM?

It is configured for dynamic storage but I have set the limit to be 8.0 GB.

---

