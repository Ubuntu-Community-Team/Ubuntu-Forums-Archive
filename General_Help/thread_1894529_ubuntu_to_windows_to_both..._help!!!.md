---
title: "ubuntu to windows to both... help!!!"
date: 2011-12-12
forum: General Help
---

### Post by ramus313 on 2011-12-12
on my desktop i have ubuntu 11.10 installed. i am experiencing difficulties with it at the moment and would like to erase the OS, install windows, then re install ubuntu. i would just install windows then re install the grub bootloader, but with the problem im having, it doesnt recognize the windows 7 iso disc(i am having the "checking battery state" problem after updating 11.10 . i have tried everything to fix it, including using livecd. the livecd boots into the purple screen, but doesnt go into the would you like to try or install page, it jsut freezes).


 i have actually already tried wiping my harddrive, but i havent had any success with that (i have tried to use Dbam and kill disk)

---

### Post by mike555 on 2011-12-12
Use the live cd, gparted can partition for Windows NTFS and for Ubuntu EXT4  plus a swap partition


 You might need to add " nomodeset " to boot by taping F6 during boot.

---

### Post by ramus313 on 2011-12-12
i managed to get a fresh install of ubuntu 11.10 working properly but the windows is still not working. i switched the BIOS to Disc first, but it still doesnt recognize the disc with the winows iso file on it and just boots into the ubuntu 11.10

---

### Post by oldtimer7777 on 2011-12-12
> **ramus313 said:**
> on my desktop i have ubuntu 11.10 installed. i am experiencing difficulties with it at the moment and would like to erase the OS, install windows, then re install ubuntu. i would just install windows then re install the grub bootloader, but with the problem im having, it doesnt recognize the windows 7 iso disc(i am having the "checking battery state" problem after updating 11.10 . i have tried everything to fix it, including using livecd. the livecd boots into the purple screen, but doesnt go into the would you like to try or install page, it jsut freezes).


 i have actually already tried wiping my harddrive, but i havent had any success with that (i have tried to use Dbam and kill disk)

I've had better luck installing Windows 7 first, and then installing Ubuntu 11.10 secondly.

---

### Post by ramus313 on 2011-12-12
yea but ubuntu 11.10 is already isntalled, if i could delete it and start compeltely fresh that would be great, but i dont know how... do i have to wipe my hard drive or something?

---

### Post by oldtimer7777 on 2011-12-12
> **ramus313 said:**
> yea but ubuntu 11.10 is already isntalled, if i could delete it and start compeltely fresh that would be great, but i dont know how... do i have to wipe my hard drive or something?

Oh that's easy.  Make sure you got your data migrated off that you want to keep and back that up into the cloud or whatever with spideroak or whatever.

Okay now you need to boot from your live Ubuntu stick of Ubuntu..    Download an iso of Ubuntu 11.10..  And then you use Startup Disc Creator to transfer that image onto your Flash Drive.  Boot your computer from that USB Flash Drive of Live Ubuntu 11.10.  

Then you need to run gparted and wipe your entire harddrive. 

Delete your partitions, all of them.   Don't use the dropdown and accidentally select your USB drive though. That would be bad. Then lastly you create a new parition table.  Click Device in gparted and then click create new partition table.   Make sure you format the hard drive to be NTFS completely.   Shutdown your USB Flash Drive of LIve Ubuntu, and install Windows 7 like you normally do from the factory OEM discs. When you are done installing Windows 7, use your live Usb of Ubuntu 11.10 to boot from and reinstall Ubuntu 11.10 again. The ubuntu installer will allow you to shrink your Windows partition, and install Ubuntu "side-by-side" with your Windows 7.  That always works perfectly for me. You will have a working grub menu this time and you will be able to choose between Windows 7 or Ubuntu each time you turn on your computer.  No worries. :)

---

### Post by ramus313 on 2011-12-13
> **oldtimer7777 said:**
> Oh that's easy.  Make sure you got your data migrated off that you want to keep and back that up into the cloud or whatever with spideroak or whatever.

Okay now you need to boot from your live Ubuntu stick of Ubuntu..    Download an iso of Ubuntu 11.10..  And then you use Startup Disc Creator to transfer that image onto your Flash Drive.  Boot your computer from that USB Flash Drive of Live Ubuntu 11.10.  

Then you need to run gparted and wipe your entire harddrive. 

Delete your partitions, all of them.   Don't use the dropdown and accidentally select your USB drive though. That would be bad. Then lastly you create a new parition table.  Click Device in gparted and then click create new partition table.   Make sure you format the hard drive to be NTFS completely.   Shutdown your USB Flash Drive of LIve Ubuntu, and install Windows 7 like you normally do from the factory OEM discs. When you are done installing Windows 7, use your live Usb of Ubuntu 11.10 to boot from and reinstall Ubuntu 11.10 again. The ubuntu installer will allow you to shrink your Windows partition, and install Ubuntu "side-by-side" with your Windows 7.  That always works perfectly for me. You will have a working grub menu this time and you will be able to choose between Windows 7 or Ubuntu each time you turn on your computer.  No worries. :)


i did it, but i little differently. i had no usb, so instead i used the live cd disk, erased the harddive, shut down, then tuned back on and loaded windows 7 disk, i also set the bios to boot from disc. and when i turn on it just opens to screen that says "loading operating system" and it stays like that. doe this mean there is something wrong with the iso file on the disc?

also, how do i make sure it is NTSF? and what exactly does that do?

---

### Post by oldtimer7777 on 2011-12-13
> **ramus313 said:**
> i did it, but i little differently. i had no usb, so instead i used the live cd disk, erased the harddive, shut down, then tuned back on and loaded windows 7 disk, i also set the bios to boot from disc. and when i turn on it just opens to screen that says "loading operating system" and it stays like that. doe this mean there is something wrong with the iso file on the disc?

also, how do i make sure it is NTSF? and what exactly does that do?

Well you did enough for the Windows disc to detect the drive at least. It would format it for you.  You would at least get a prompt with the Windows Installation cd.  Note: Windows Installation can take a considerable time to boot up. 

Did you download this Windows 7 from a torrent site or is it a silver pressed cd from the factory?

---

### Post by ramus313 on 2011-12-13
im going to be honest i did download it from a torrent site,  cuz im getting an ubuntu laptop  (which i plan to get licensed windows for dualboot :))soon and ive actually never used windows of any kind on a personal computer, and i wanted to dual boot on my desktop to kind of get a feel for it before i decide if i really want to spend ~$100-$150 on it. 

so all i have on the disc is the iso file itself. do i need anything else in order to get it running properly?

---

### Post by Bucky Ball on 2011-12-13
Install Windows when you can on a partition big enough for it, leaving the rest of the drive free space (or leave whatever other partitions are on there, matters not). Win install will format to NTFS, you don't have to worry about that. Ubuntu install will format its partitions (EXT4) on the rest of drive, you don't have to worry about that, either.

---

### Post by oldtimer7777 on 2011-12-13
You are going to need to buy windows discs if you want to install Windows properly.  

Stick with Ubuntu until you can afford it.  After a while you may decide you don't really need Windows after all too.  I stopped using Windows entirely over 3 years ago and I very rarely need to use it except for specialized projects that require me to use Windows for something. 

You can test your iso of windows in VMWare on Ubuntu OS for now:

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

That's as good as it is going to get for your situation for right now.

> **ramus313 said:**
> im going to be honest i did download it from a torrent site,  cuz im getting an ubuntu laptop  (which i plan to get licensed windows for dualboot :))soon and ive actually never used windows of any kind on a personal computer, and i wanted to dual boot on my desktop to kind of get a feel for it before i decide if i really want to spend ~$100-$150 on it. 

so all i have on the disc is the iso file itself. do i need anything else in order to get it running properly?

---

### Post by ramus313 on 2011-12-13
k thanks for your help

---

### Post by nothingspecial on 2011-12-13
Pirated software is not supported here.

Closed.

---

