---
title: "Problems With Virtualbox"
date: 2010-02-12
forum: General Help
---

### Post by joelandsonja on 2010-02-12
I was wondering if anyone else had the following problem with Virtualbox ...

I have installed Windows XP (Home) into Virtualbox, and for some reason there are a few drivers that won't install correctly, therefore my emulators will not play any video or plugin capabilities. 

I get the following errors for my system drivers. 

The 'SCSI Controller' cannot find it's driver.
The 'PCI Device' cannot find it's driver.
The 'Video Controller (VGA Compatible)' cannot find it's driver.
The 'Base System Device' cannot find it's driver. 

I have tried installing the video driver directly from Nvidia's website (For the GT 220 graphics card) but for some reason it refuses to install on Virtualbox. I downloaded Driver Detective to help with the problem, but of course they won't fix it unless I pay them $40 ... which I'm not even certain would fix the problem. 

Does anyone know how to fix these problems?

* On a side note, I already tried changing the settings in the 'System > Administration > Users & Groups > Changing Settings for Virtual box trick ... didn't work ...

* Also, the correct check boxes appear to be enabled in the Virtualbox menus, USB is enabled and a filter is added ... graphics are enabled ... nothing seems to work.

---

### Post by kmrs75 on 2010-02-12
correct me if im wrong but thoes are all your hardware drivers - if you know what each is you can probable find them online and down load them 

what is the manufacture if the computer and the model of the computer 

go to there website and look for the harware specs for that model or serial number then they should have the correct drivers for you

---

### Post by bruno9779 on 2010-02-12
I don't think you can emulate a graphic card that doesn't exist physically.

If you have a graphic card only, then the host system will be using it, leaving you with a limited (virtual) version of an OS.

The same happens if you run ubuntu in a VM in Win: no way to turn compiz on and make it work (the 3D part at least).

I have never tried having a dedicated 2nd graphic card to give 3D support to a virtual machine, but I have seen XP images run with 3D support on ubuntu server (no gui, automatically loads image on VMware)

---

### Post by joelandsonja on 2010-02-13
I was finally able to install the guest additions into Virtualbox which made most of my emulators work, but I am not able to run any games in 3D. (Mostly Project 64)

I keep getting the error message. "Failed to intialize Direct3d" ... this happens despite the fact that I have the most current version of Directx installed. 

Any thoughts?

---

### Post by falconindy on 2010-02-14
Sounds like you haven't installed the guest additions.

---

### Post by kmrs75 on 2010-02-14
i have addons installed and mine does the same thing will not start 3D im not at home but i think the error is something like not suported - i dont need it so i just shut off the 3D graphics

---

### Post by Richard1979 on 2010-02-14
> **kmrs75 said:**
> i have addons installed and mine does the same thing will not start 3D im not at home but i think the error is something like not suported - i dont need it so i just shut off the 3D graphics

You're not going to be playing proper DirectX games in a VM this year at least.
VirtualBox is probably on the cutting edge of VM tech and they do support *some* 3D but I wouldn't expect to be playing Modern Warfare 2 any time soon.

Install the additions - the Windows installation should detect and install the "virtual" graphics card that is running VirtualBox - it most likely won't know about your Nvidia card.

---

### Post by joelandsonja on 2010-02-14
Hmm ... I have installed the guest services pack, but it didn't make any difference. 

I'm not trying to play anything too complicated, only a Nintendo 64 and Playstation 1.

I don't know what to do at this point ...

---

