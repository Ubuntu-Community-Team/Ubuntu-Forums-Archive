---
title: "Multi booting a USB Drive"
date: 2009-12-25
forum: General Help
---

### Post by Pesky_Programmer on 2009-12-25
I would like to make myself an emergency bootable flash drive so if ever the unfortunate should happen and my computer melts down I can easily fix it. This is my first time attempting to do something like this.
 
I have already been doing some research and read some of the information at this site [http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/) and have tried many of the boot loaders. So far they have all done exactly what they said they would:). 
 
I first tried booting ISO files and that one worked for the most part except I could not run an operating system live. I tried both DSL and Xubuntu (xubuntu-8.04.1-desktop-i386.iso) and neither would boot to a graphical desktop. However the memory test worked just fine and I was able to edit grub to load multiple ISO files.
 
So I did some more reading and tried the USB boot tool for xubuntu 9.04 on my xubuntu ISO and was successfully able to boot into xubuntu. But this method only supports the one operating system and I have some other ISO files I would like to be able to boot from.
 
After a few more hours of research on the web I began to read up on how to manually configure grub onto my usb drive. Except one thing I have been unable to find is how do I know what file to tell grub to read from my drive to boot the OS. 
For example:
 
>  
title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=3adabece-a770-49a0-bf76-766193ae1204 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault
 

 
I pulled this from a form talking about Grub; If I installed grub to my flash drive, how do I know what to put into the Kernel line to start the OS booting and what other lines would I need to add to specify the OS I am booting? 
 
Also noticed that when I look at my usb Drive in gparted( with my currant ubuntu install on my HD) it displays as (sdb1) but when I configured My USB drive with the ISO booter it displays like this:
 
>  
title Memtest86+
find --set-root /memtest86+-4.00.iso
map --mem /memtest86+-4.00.iso (hd32)
map --hook
root (hd32)
chainloader (hd32) 

 
Why does (hd32) work for declaring my usb drive when it is displayed as (sdb1) in Ubutnu? Also would that not mean my USB drive is being declared as a Hard Drive when it is not hooked up as one?
 
I hope I have explained myself clearly and apologize for the length, thanks for reading.:)
 
I will restate my questions here so you don't have to pick them out of my long post::P
 
How would I tell Grub to load Xubuntu from my flash drive, what lines would I need in the grub loader?
 
Is there any way to figure this information out I.E. can I come to a logical conclusion on what files need to be specified by just looking at the OS file system?
 
Why does the grub ISO loader specify my drive as (hd32) and work when everything I have read about GRUB seams to say thats wrong?

---

### Post by QrK0 on 2009-12-28
I find this a little bit confusing but I finnally could get a multi-bootable usb.
When you start the system booting from the usb, the usb becomes the first device. In grub, the first device or disk is hd0. So in this case, the usb is the disk hd0
But when you starts the system booting from the internal hard disk, the hard disk becomes the first disk, that is, hd0 in grub.
This is due the BIOS settings

---

### Post by Pesky_Programmer on 2009-12-30
[COLOR=black][FONT=Verdana]QrK0: thanks for the tip . [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Using that and some of what I have been learning about grub I have been able to specify my usb drive in the grub on my hard drive. The entry looks something like this.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]title second disk[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]rootnoverify (hd1)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]chainloader +1[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Using this method allows me to boot from my 1 GB flash drive (that for some unknown reason would not boot otherwise), and also allows me decide what to boot without having to go into my bios every time. Previously I could only boot my 8 GB sandisk drive.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]As far as I can tell this method will boot just about any OS from a bootable device (so long as you change "(hd1)" to specify the appropriate device). I have also learned that in order to make a flash drive a multi boot drive it must be partitioned accordingly no differently then you would your HD. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I also noticed, and I assume this is true on all systems, that Windows XP will only detect the first partition on a flash drive. So if you are using your flash drive for both storage and booting as I am; It is best to make the first partition storage so you can access it on Windows platforms. However Ubuntu seams to have no problem detecting both partitions so if you are using only unix platforms it probably wont matter.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Other then my initial experimenting I have not set up my flash drive completely and will post how it turns out later, as a reference for others who are attempting the same. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Here is a list of what I plan to add to my multi boot flash drive. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Slax[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]gparted live[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]xubuntu\dsl[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am still searching for a windows recovery console that will work on a flash drive, so far every windows tool I have used crashes when booted from a usb drive or gets stuck trying to mount the cd drive. If anyone could tell me where to find one that works it would be greatly appreciated. Or a way to partition my usb drive as a read only cd drive (which may circumvent the problem). I know that my sandisk drives came that way originally with the U3 software but am unsure on how to set this up myself.[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]Hopefully my next post will be an easy to follow step by step tutorial for beginners on this topic.[/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

