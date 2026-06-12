---
title: "I need serious help I cant unistall ubuntu...plzz"
date: 2011-06-20
forum: General Help
---

### Post by Setir on 2011-06-20
I need to use xp, but I cant unistall ubuntu I dont why , I had tried a lot of thing and nothing, I put a iso in a cd but the cd doesnt boot, I put a iso to a usb , and it doesnt boot, I had tried to used super grub disk with unetbootin but nothing happen, I tried to gparted and delete but I cant , I had been trying 3 days and nothing, I help serious help plz

---

### Post by inameiname on 2011-06-20
> **Setir said:**
> I need to use xp, but I cant unistall ubuntu I dont why , I had tried a lot of thing and nothing, I put a iso in a cd but the cd doesnt boot, I put a iso to a usb , and it doesnt boot, I had tried to used super grub disk with unetbootin but nothing happen, I tried to gparted and delete but I cant , I had been trying 3 days and nothing, I help serious help plz

I take it your current machine has both Ubuntu and Windows XP installed? And your question is how to remove just the Ubuntu part? Or are you simply trying to remove everything so you can install Windows XP? If removing everything is what you want, there are plenty of simply wiping applications that run from disk that work well for that, such as Kill Disk.

Or is it that nothing's working, and you cant run any type of disk/drive/flash drive at startup. Is that what your issue is?

---

### Post by nzjethro on 2011-06-20
Hi Setir, welcome to the forums. Could you please provide us with more information. Do you currently have just Ubuntu installed, and are trying to remove it and install xp?

I suggest that you try to change your boot order in your BIOS menu, by pressing esc or F12 or something when your computer turns on. In this menu, move CD and USB above hard-drive and see whether that makes a difference.

---

### Post by Setir on 2011-06-20
nop, when I installed ubuntu my windows 7 part disappear , now I only have ubuntu

---

### Post by inameiname on 2011-06-20
I see. I guess my first question is when you installed Ubuntu, where it asked if you wanted to install alongside Windows XP or erase and install using the whole disk, you picked the former, right? I'm sure you did, but its something that sometimes gets mischecked and that screws things up obviously. 

If that happened, Windows is gone. If that's not the issue, then maybe somethings wrong with the boot menu. Just follow [nzjethro]("http://ubuntuforums.org/member.php?u=1306925")'s advice.

---

### Post by Setir on 2011-06-20
> **inameiname said:**
> I take it your current machine has both Ubuntu and Windows XP installed? And your question is how to remove just the Ubuntu part? Or are you simply trying to remove everything so you can install Windows XP? If removing everything is what you want, there are plenty of simply wiping applications that run from disk that work well for that, such as Kill Disk.

Or is it that nothing's working, and you cant run any type of disk/drive/flash drive at startup. Is that what your issue is?

my problem is that I have full ubuntu installed, and I need now windows 7, I had put the .iso to my usb and nothing happens, the .iso to the cd and it doesnt boot it, then I used super grup disk with unetbootin , but super grup disk never boot.

I changed the bios for the usb and the cd.

---

### Post by Setir on 2011-06-20
> **inameiname said:**
> I see. I guess my first question is when you installed Ubuntu, where it asked if you wanted to install alongside Windows XP or erase and install using the whole disk, you picked the former, right? I'm sure you did, but its something that sometimes gets mischecked and that screws things up.


yeah I did that mistake.

---

### Post by slooksterpsv on 2011-06-20
> **Setir said:**
> my problem is that I have full ubuntu installed, and I need now windows 7, I had put the .iso to my usb and nothing happens, the .iso to the cd and it doesnt boot it, then I used super grup disk with unetbootin , but super grup disk never boot.

I changed the bios for the usb and the cd.

The Windows 7 iso? Is that what you mean?

If you put the Windows 7 iso on the USB, there's a very specific way you have to put it on the USB to get it to work. If you burned it to a CD you need to use a program like Brasero to burn the iso to a CD (as just copying to the CD doesn't do anything but make a file and not the actual specifics for booting from the cd).

Otherwise, I'm lost.

If you could explain, if I didn't get the above right, what ISO you are meaning, and how you tried to put it on various mediums.

---

### Post by inameiname on 2011-06-20
The thing I'm a bit confused about is your issues with your discs and flash drives screwing up at startup. Whether you have Ubuntu or Windows XP or whatever is of no importance for those things, as the OS only gets booted after those devices. That is, if you have a disk drive / usb boot as first before the hard drive. If not, change that using the method mentioned above. 

If there is still an issue, and the disks aren't booting, then its a bad image on the disk, and/or bad copy, IDK.

---

### Post by Setir on 2011-06-20
> **slooksterpsv said:**
> The Windows 7 iso? Is that what you mean?

If you put the Windows 7 iso on the USB, there's a very specific way you have to put it on the USB to get it to work. If you burned it to a CD you need to use a program like Brasero to burn the iso to a CD (as just copying to the CD doesn't do anything but make a file and not the actual specifics for booting from the cd).

Otherwise, I'm lost.

If you could explain, if I didn't get the above right, what ISO you are meaning, and how you tried to put it on various mediums.

Im using the windows 7 32 bit.iso  I put use live usb and unetbootin to try to boot the usb but it desnot work idk why.

I will put an example , unetbootin and live usb they start and they go to a interface were it say it will boot in 10 seconds but it never boot idk why

---

### Post by slooksterpsv on 2011-06-20
> **Setir said:**
> Im using the windows 7 32 bit.iso  I put use live usb and unetbootin to try to boot the usb but it desnot work idk why.

Nope it won't. The reason is, with Unetbootin it looks for a kernel to load, a Linux kernel, that's how it pushes all the startup through. With Windows, it has no such kernel (it has one but not a linux one) and Unetbootin doesn't know how to make devices for booting from USB for Windows CD/DVDs.

I'd suggest burning the iso using Brasero to a DVD. The reason? The way to get it to work on USB in Ubuntu is tough and takes a lot of time and patience - I don't know if I ever got it to work or not, I think I did after about 20+ tries (approx 16 hours worth of trying).

EDIT:
[http://www.linuxquestions.org/questions/linux-software-2/creating-windows-7-bootable-usb-from-linux-762229/](http://www.linuxquestions.org/questions/linux-software-2/creating-windows-7-bootable-usb-from-linux-762229/)

Just for reference, but it is difficult and time-consuming.

---

### Post by Setir on 2011-06-20
> **slooksterpsv said:**
> Nope it won't. The reason is, with Unetbootin it looks for a kernel to load, a Linux kernel, that's how it pushes all the startup through. With Windows, it has no such kernel (it has one but not a linux one) and Unetbootin doesn't know how to make devices for booting from USB for Windows CD/DVDs.

I'd suggest burning the iso using Brasero to a DVD. The reason? The way to get it to work on USB in Ubuntu is tough and takes a lot of time and patience - I don't know if I ever got it to work or not, I think I did after about 20+ tries (approx 16 hours worth of trying).

well thx I will try that tommorrow I will try to burn the iso with brasero

another question why I tried to use super grub disk from usb and it never boot it?

---

### Post by inameiname on 2011-06-20
Indeed. Its just not worth the hassle to do that to have Windows 7  installable via USB. Although, saying that, I found this:  [http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx) or  [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/).  Obviously haven't tried it since I just found it, so I don't know if  its easy or not.

Also, just remember when you get a working Windows 7.iso and are able to  install it via disc, I don't believe you can simply install Windows 7 and leave Ubuntu. At least it used to be that way. Not sure about Windows 7. It thinks its the only system, so it screws up bootloader and such. Although, there is a method using Gparted within Ubuntu: [http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/](http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/), but this is probably get a bit too confusing at the moment, so I should stop. Hehe

---

### Post by Setir on 2011-06-20
> **inameiname said:**
> Indeed. Its just not worth the hassle to do that to have Windows 7  installable via USB. Although, saying that, I found this:  [http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx) or  [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/).  Obviously haven't tried it since I just found it, so I don't know if  its easy or not.

Also, just remember when you get a working Windows 7.iso and are able to  install it via disc, I don't believe you can simply install Windows 7 and leave Ubuntu. At least it used to be that way. Not sure about Windows 7. It thinks its the only system, so it screws up bootloader and such. Although, there is a method using Gparted within Ubuntu: [http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/](http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/), but this is probably get a bit too confusing at the moment, so I should stop. Hehe

in gparted I only have one /dev/sda , that is my main disk and the only one I have, I delete the other the linux-swap and the other ext , trying to delete umuntu , Idk if I did a mistake or what

---

### Post by Setir on 2011-06-20
another thing is that I used the iso of super grub disk to a cd and it never boot...

---

### Post by inameiname on 2011-06-20
> **Setir said:**
> in gparted I only have one /dev/sda , that is my main disk and the only one I have, I delete the other the linux-swap and the other ext , trying to delete umuntu , Idk if I did a mistake or what

You mean you just now deleted the extended and linux-swap from /dev/sda? If so, that is not good. All three ARE Ubuntu. And also if so, you just formatted your hard drive and removed parts of Ubuntu. Once you restart your computer, it will fail and you need to install an OS. Definitely back things up before restarting if that happened. I am sorry if I confused you there and got you onto that idea. It was just an option.

Basically what it comes down to is if you care to keep your current Ubuntu installation or not. If not, first install Windows 7.iso on a disk, install it, and then install Ubuntu afterwards. But if you did do the above, I don't know what to tell you. There are options, but I'd have to really look into it to figure out them.

And regarding Super Grub Disk, if you simply installed the iso downloaded from its site and burned it to a disc, IDK what to tell you. Unless the burn was bad, it should at least run at startup.

---

### Post by Setir on 2011-06-20
> **inameiname said:**
> You mean you just now deleted the extended and linux-swap from /dev/sda? If so, that is not good. All three ARE Ubuntu. And also if so, you just formatted your hard drive and removed parts of Ubuntu. Once you restart your computer, it will fail and you need to install an OS. Definitely back things up before restarting if that happened. I am sorry if I confused you there and got you onto that idea. It was just an option.

Basically what it comes down to is if you care to keep your current Ubuntu installation or not. If not, first install Windows 7.iso on a disk, install it, and then install Ubuntu afterwards. But if you did do the above, I don't know what to tell you. There are options, but I'd have to really look into it to figure out them.

And regarding Super Grub Disk, if you simply installed the iso downloaded from its site and burned it to a disc, IDK what to tell you. Unless the burn was bad, it should at least run at startup.

I did that because  saw in a video of youtube that one guy deleted the 3 things , but I only could delete 2 things the ext and the linux, and I saw that when he delete the 3 things his windows was back again..

---

### Post by Setir on 2011-06-20
so if I deleted those 2 thing I will have ubuntu for ever?

---

### Post by inameiname on 2011-06-20
> **Setir said:**
> I did that because  saw in a video of youtube that one guy deleted the 3 things , but I only could delete 2 things the ext and the linux, and I saw that when he delete the 3 things his windows was back again..

I see. I take that then you want Ubuntu gone for now. If that's the case, it doesn't matter, so long as you have Windows 7 ready on a disk for you to install. 

Unlike Windows, which uses only one partition on the device, Ubuntu makes 3, /dev/sda1 (ext4), /dev/sd2 (extended), and /dev/sd3 (linux-swap). Using Gparted to get rid of all of those is not really the right way to do that. Not sure if it actually does it entirely. The simplest way is to just install Windows 7, and during installation delete any partitions already existing, and voila. Or use Kill Disk or other wiping program to completely wipe the hard drive to factory clean, and then install Windows.

FYI, you can't delete /dev/sd1 because you are running it. I'm sure the kid on Youtube was able to because he deleted the three on the hard drive by running a Live CD with gparted installed on it to do all of that. Just a guess.

Either way, that's not really the issue. I'm just sort of confused about things most of this thread and trying to better understand. You want Windows 7 on now, dont care about Ubuntu at this time, until Windows 7 is on; after that, you can reinstall Ubuntu. Good enough method in my opinion.

---

### Post by inameiname on 2011-06-20
> **Setir said:**
> so if I deleted those 2 thing I will have ubuntu for ever?

Huh? No, if you deleted those, Ubuntu's gone. Well, parts of it. You will have it forever as far as being unable to do anything with it until you completely erase it, either through an Ubuntu Live CD or by installing Windows 7.

---

### Post by Setir on 2011-06-20
> **inameiname said:**
> I see. I take that then you want Ubuntu gone for now. If that's the case, it doesn't matter, so long as you have Windows 7 ready on a disk for you to install. 

Unlike Windows, which uses only one partition on the device, Ubuntu makes 3, /dev/sda1 (ext4), /dev/sd2 (extended), and /dev/sd3 (linux-swap). Using Gparted to get rid of all of those is not really the right way to do that. Not sure if it actually does it entirely. The simplest way is to just install Windows 7, and during installation delete any partitions already existing, and voila. Or use Kill Disk or other wiping program to completely wipe the hard drive to factory clean, and then install Windows.

FYI, you can't delete /dev/sd1 because you are running it. I'm sure the kid on Youtube was able to because he deleted the three on the hard drive by running a Live CD with gparted installed on it to do all of that. Just a guess.

Either way, that's not really the issue. I'm just sort of confused about things most of this thread and trying to better understand. You want Windows 7 on now, dont care about Ubuntu at this time, until Windows 7 is on; after that, you can reinstall Ubuntu. Good enough method in my opinion.

if I reinstall ubuntu windows 7 will come back?
how I do that with a live usb with ubuntu?

---

### Post by inameiname on 2011-06-20
> **Setir said:**
> if I reinstall ubuntu windows 7 will come back?
how I do that with a live usb with ubuntu?

I think I'm confusing you. At this moment, Windows 7 will not come back. Period. Ubuntu will not come back. Period. What is currently there is a corrupted Ubuntu on your computer, as you've removed two of its three partitions. Therefore, its pretty much gone. 

Now, the only way to proceed now is to either get your Windows 7 disc ready (burn iso to a disc) OR have a Ubuntu live usb/cd on hand/burned. 

If you don't have a Windows 7 disc made, make it.
If you can't make it, restart and run the live usb of Ubuntu, and inside it, create the Windows 7 disc.
Once you have Windows 7 disc made, install it. 
And once you are done there, install Ubuntu to your hard drive, using the live usb (remember to select install alongside Windows this time).
Once Ubuntu is installed, you will then have both Windows 7 and Ubuntu on there.

---

### Post by BLTicklemonster on 2011-06-20
> **Setir said:**
> yeah I did that mistake.

I find it interesting that Ubuntu still hasn't made the installation dialogue flat out plain that you either want option A or option B with all it's various contingencies. A wipe it all and just put ubuntu in, or B Don't Lose My Windows, Please, but I do want to install ubuntu, thanky very much.

There's an extra step that needs to be put in there, and if they choose option B, then the windows partion(s) (or other OSs of course) should become inaccessible.

---

### Post by westie457 on 2011-06-20
> **inameiname said:**
> I think I'm confusing you. At this moment, Windows 7 will not come back. Period. Ubuntu will not come back. Period. What is currently there is a corrupted Ubuntu on your computer, as you've removed two of its three partitions. Therefore, its pretty much gone. 

Now, the only way to proceed now is to either get your Windows 7 disc ready (burn iso to a disc) OR have a Ubuntu live usb/cd on hand/burned. 

If you don't have a Windows 7 disc made, make it.
If you can't make it, restart and run the live usb of Ubuntu, and inside it, create the Windows 7 disc.
Once you have Windows 7 disc made, install it. 
And once you are done there, install Ubuntu to your hard drive, using the live usb (remember to select install alongside Windows this time).
Once Ubuntu is installed, you will then have both Windows 7 and Ubuntu on there.


Hello, Everything in the quoted above is correct.

The Windows install DVD as far as I can remember is the only one that overrides the boot order in the BIOS. When burned correctly and put to use you will have a blank screen with a line of text that says "Press any key to boot from CD\DVD. 
If you do not see that, it has not burned correctly and will need to be burned again.

This is fresh in my mind as I stuffed my spare PC a couple of days ago.

---

### Post by nzjethro on 2011-06-20
> **BLTicklemonster said:**
> 
There's an extra step that needs to be put in there, and if they choose option B, then the windows partion(s) (or other OSs of course) should become inaccessible.

I agree. First time installing Ubuntu 10.10 I accidentally wiped Windows off of my HDD. I was lucky  I had backed up, and that I legitimately wanted Ubuntu to (eventually) be my only OS, 'cos if I had have wanted to keep Win 7 around, that probably would have put me off Ubuntu/Linux for life.

---

### Post by inameiname on 2011-06-20
> **westie457 said:**
> Hello, Everything in the quoted above is correct.

The Windows install DVD as far as I can remember is the only one that overrides the boot order in the BIOS. When burned correctly and put to use you will have a blank screen with a line of text that says "Press any key to boot from CD\DVD. 
If you do not see that, it has not burned correctly and will need to be burned again.

This is fresh in my mind as I stuffed my spare PC a couple of days ago.

Yep. Thanks for adding to what I wrote. Hopefully the threader will better understand things now.

---

