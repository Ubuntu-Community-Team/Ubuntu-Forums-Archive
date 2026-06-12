---
title: "UUID does not exist..."
date: 2010-01-26
forum: General Help
---

### Post by fschnittke on 2010-01-26
Hi:

I installed the latest (9.10) Ubuntu on a compact flash card. Everything works fine. Now, I want to put that flash card into different PC's and it will not boot. It goes past loading grub, then I get a black screen with a cursor. If I do CTRL-ALT-F1, I can see the error message on the screen:

ALERT! /dev/disk/by-uuid/a0d619fe-6386-42c4-9832-52b46acf7656 does not exist. Dropping to a shell!

And there it puts me into busybox.

I thought because the drive is in a different pc and connected to a different controller, that the uuid is now different. This is not the case. I booted off a CD and ran blkid, and the uuid is still the same.

So why won't it boot?

It's a 4Gb compact flash card connected to a SATA to CF converter. I tried editing the grub command to remove the uuid and replace it with /dev/sda1, but this did not work either.

Any help would be appreciated.




Fred

---

### Post by fschnittke on 2010-01-27
Well, I can't says I got a lot of help on this, but I did manage to resolve my issue, and learn alot. 
 
I don't think I mentioned in the previous post that I was using a kernel provided by the makers of FIT-PC2. I loaded this kernel in order to get the Intel GMA 500 Video drivers. That all worked without any problem, but as soon as I pulled the drive out and put it in another machine, that's when I got the error.
 
I learnt that the /proc/modules file was empty. I didn't realize it was created dynamiclaly upon boot up and that it was populated with modules provided by the kernel. In my case the FIT-PC2 kernel only had modules for their hardware. Thus when I put the disk in another machine, it could not detect the hardware and boot off the drive.
 
My resolution was to copy over a generic linux kernel (the FIT-PC2 installation process removed them), then edit my menu.lst to reflect the new generic linux kernel.
 
 
Fred

---

### Post by Leppie on 2010-01-27
> **fschnittke said:**
> I loaded this kernel in order to get the Intel GMA 500 Video drivers. That all worked without any problem, but as soon as I pulled the drive out and put it in another machine, that's when I got the error.
this is generally considered as *[COLOR=Red]**not**[/COLOR]* good practice, even windows doesn't support this kind of action

---

### Post by mcduck on 2010-01-27
Perhaps it's not actually complaining about your flash memory's UUID, but instead about missing some drive that was connected to your computer at the time when you did the install? Check your /etc/fstab..

Anyway, making a normal Ubuntu install to a flash drive isn't really a good way if you want to make the system portable. What you really want is something that detects all the available hardware on every boot instead of assuming the hardware that you had at the time when you made the install.

For that kind of Ubuntu installs you should use the "USB Startup Disk Creator" that you can find in System/Adminsitration menu. Just tell it to reserve the available extra space on your drive for storing documents and settings, and you'll get a proper portable Ubuntu that will work on different computers but still allows you to install programs, customize settings and store your persona files.

---

### Post by fschnittke on 2010-01-28
Thanks for your replies. This was an experiment to see what would happen when the ubuntu image was placed on another machine. We are looking at rolling out 1000 of these machines as nettop devices where the operating system would be write protected using aufs. Once the machine is on location, all it will ever do is connect to one website and display flash videos connected to a HDTV in our Client's waiting rooms.

So, moving the image to another machine may not be a good idea, but in this situation it's a darn good idea. For the most part the hardware will remain the same, but I'm sure by the 1000th one, there will be some hardware changes, and that's what this test was all about.

Windows actually does allow you to move a hard drive from one machine to another, provided the hardware platform is the same. If not, there is a utility called sysprep that will do the trick.

Thanks for your suggestions...

---

### Post by Leppie on 2010-01-28
> **fschnittke said:**
> Windows actually does allow you to move a hard drive from one machine to another, provided the hardware platform is the same. If not, there is a utility called sysprep that will do the trick.
what does "the hardware platform is the same" mean to you? i have tried booting into a windows install after upgrading a cpu and it didn't work. i am not talking about switching from intel to amd or something similar, but intel to intel or amd to amd. cpu architectures may be very different though still the same platform and same manufacturer.

and what is doable is not also "meant to be done or possible".

---

### Post by mcduck on 2010-01-28
> **fschnittke said:**
> Thanks for your replies. This was an experiment to see what would happen when the ubuntu image was placed on another machine. We are looking at rolling out 1000 of these machines as nettop devices where the operating system would be write protected using aufs. Once the machine is on location, all it will ever do is connect to one website and display flash videos connected to a HDTV in our Client's waiting rooms.

So, moving the image to another machine may not be a good idea, but in this situation it's a darn good idea. For the most part the hardware will remain the same, but I'm sure by the 1000th one, there will be some hardware changes, and that's what this test was all about.

Windows actually does allow you to move a hard drive from one machine to another, provided the hardware platform is the same. If not, there is a utility called sysprep that will do the trick.

Thanks for your suggestions...

So you are not actually trying to do a portable install? In that case there should be no problems, Ubuntu is actually far more portable to different hardware than Windows is, since most of the drivers are included by default, the only ones that might cause problems when moving from one system to another comletely different one are graphics drivers (like when changing from Ati to nVidia, for example). Windows is really famous of *not being portable* if there's any difference in the hardware.

You just have to make the install correctly, meaning that you don't want to have any extra hard drives on the machine where you do the original install (since those drives would get entry in /etc/fstab), but I can't really tell if that was what caused your problem with the given information.

Anyway, if you post the /etc/fstab file and outputs of "blkid" and "sudo fdisk -l" commands from the machien I'm sure weä'll be able to figure out what's causin your UUID error.

Anyway,

---

### Post by fschnittke on 2010-01-28
Hi mcduck:

As noted in my second post. The problem is resolved. The problem was the proprietary kernel provided by FIT-PC2, which didn't contain the necessary modules to get the system up and running when the drive was inserted into another machine.

I was able to reload the original linux-generic kernel on the second machine, install the video drivers (for that machine), and it's working fine.

Essentially I took a UBUNTU image from one machine, loaded it on another, made a few kernel/video driver changes , and life is good....

For Leppie:

You can ghost windows images to machines with similar hardware, and sometimes you can't. I know when Windows is installed, the OS ties itself to serial numbers in the CPU, board, etc. I've ghosted Windows between "similar" machines many of times. Sometimes it doesn't work because the hardware is too different, then you have to resort to using the SYSPREP utility provided by Microsoft.

Other than that, if it works, who cares if it's meant to be.....

---

