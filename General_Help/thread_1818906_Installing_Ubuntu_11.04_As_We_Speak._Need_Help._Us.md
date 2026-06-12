---
title: "Installing Ubuntu 11.04 As We Speak. Need Help. Used UNetBootin"
date: 2011-08-05
forum: General Help
---

### Post by Viva en Grey on 2011-08-05
Alright, so I originally had a very detailed post typed out..but I lost it, so I'll keep this short & sweet.


1) I'm using UNetBootin as my installation method to install Ubuntu 11.04

2) I have successfully booted using UNetBootin, and now need to officially install Ubuntu.

3) For clarity, I'll use some images to guide through. Here's where I  have started-- on my desktop is the icon for the installer of Ubuntu,  highlighted.

[IMG]http://i1184.photobucket.com/albums/z333/VivaEnGrey/Screenshot-InstallUbuntu.png[/IMG]


4) After clicking the installer, I am asked what language I would like, and am then shown this screen.

[IMG]http://i1184.photobucket.com/albums/z333/VivaEnGrey/ScreenshotAllocateDriveSpace.png[/IMG]


This is where I am kind of lost. I know that I am running Windows Vista  Home Premium 32-bit, and have ~60 GBs of files, programs, etc. I'm not  sure what drive I should select to go onward, or what I should do at all  from this point really. I would not mind completely installing Linux  over Vista, but keeping my files is a definite must. Help, anyone?

Thank you, and of course, I'm here to provide any & all screen shots and info needed!!

---

### Post by thunderbirdje on 2011-08-05
> **Viva en Grey said:**
> 
This is where I am kind of lost. I know that I am running Windows Vista  Home Premium 32-bit, and have ~60 GBs of files, programs, etc. I'm not  sure what drive I should select to go onward, or what I should do at all  from this point really. I would not mind completely installing Linux  over Vista, but keeping my files is a definite must. Help, anyone?

Thank you, and of course, I'm here to provide any & all screen shots and info needed!!

Hello Viva en Grey!

First you should decide what you would like to do: install Ubuntu besides your Windows or only Ubuntu and thereby erasing the whole hard drive).

Secondly, what I alsways do is writing down the number of hard drives/partitions in Windows together with the size (total size, used, free, ...). So it's easier to detect at the point where you are which drive is which. 

There is also a logical system (if I can quote another [post]("http://www.frihost.com/forums/vt-36885.html")): [HTML]Yeah, IDE hard disks (well, devices, actually) are hd<drive><partition>. SCSI devices (and kernel-level emulation of SCSI devices, like USB devices or, in some cases, CD-RW drives) are sd<drive><partition>. 
The standard partitioning scheme nowadays is (assuming your drive is hda): 
Code:
hda1 => bootloader and kernel(s) 
hda2 => swap space 
hda3 => root filesystem[/HTML]

There are also a lot of tutorials online if you want to dual or single boot. I've used the automatic partition manager the first time for a dual boot. When I was brave enough to take the jump, If's erased Windows (and then my good computer days started :D)

Good luck!

ps: I couldn't open your pictures, I'm in China at the moment and it seems to be blocked bu the GFW. I'm sorry for that.

---

### Post by Viva en Grey on 2011-08-05
Ah, it would be helpful if you could see the images ha. Hold on, I'm sending you a PM!

---

