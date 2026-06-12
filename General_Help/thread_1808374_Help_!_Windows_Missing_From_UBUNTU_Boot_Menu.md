---
title: "Help ! Windows Missing From UBUNTU Boot Menu"
date: 2011-07-20
forum: General Help
---

### Post by Geroman21 on 2011-07-20
Would appreciate any advice or help as I have used ubuntu or a while and  really like it but dont really undrstand the Boot Menu or Grub Menu.

I had a Duel Boot set up on my Computer Windows XP Pro was installed First and then Ubuntu.

Originally  it was just Two options listed to choose on start up when I Booted up,  this was Windows XP Pro or Ubuntu , if I did nothing Windows Xp Pro  would start Automatically after about 20 seconds.

A few months  ago boot menu became messed up and when I started the computer it would  go staight to the Grub Menu Linux Menu similar to below :
  	 	 	 	p { margin-bottom: 0.21cm; }  Ubuntu, with Linux 2.6.32-33-generic-pae +  
 Ubunu, with Linux 2.6.32-33 generic -pae (recovery  mode)
 Ubunu, with Linux 2.6.32-32 generic -pae  
 Ubunu, with Linux 2.6.32-32 generic -pae  (recovery mode)


Windows  XP Pro was now at the bottom of the list and I had to scroll down to  the bottom of the list to select it and if I did nothing it would  Automatically boot into Ubuntu.


Last  night as I was scrolling down the List I accidentally hit enter it  tried to load up Ubuntu and froze I restarted my computer and now  Windows Xp is no longer on the list !

It loads up Ubuntu fine but I can no longer boot into Windows as it is not listed when I start up.


I ran  sudo os-prober  from Terminal 

and it came back with :

/dev/sdb1:Microsoft Windows XP Professional:Windows:chain
alan@alan-desktop:~$ 

Please Help !

Alan

---

### Post by nothingspecial on 2011-07-20
Try running ```
sudo update-grub
```

See if that fixes it.

---

### Post by Geroman21 on 2011-07-20
I have run the  sudo update-grub :

Generating grub.cfg ... Found linux image: /boot/vmlinuz-2.6.32-33-generic-pae Found initrd image: /boot/initrd.img-2.6.32-33-generic-pae Found linux image: /boot/vmlinuz-2.6.32-32-generic-pae Found initrd image: /boot/initrd.img-2.6.32-32-generic-pae Found linux image: /boot/vmlinuz-2.6.32-31-generic-pae Found initrd image: /boot/initrd.img-2.6.32-31-generic-pae Found linux image: /boot/vmlinuz-2.6.32-30-generic-pae Found initrd image: /boot/initrd.img-2.6.32-30-generic-pae Found linux image: /boot/vmlinuz-2.6.32-29-generic-pae Found initrd image: /boot/initrd.img-2.6.32-29-generic-pae Found linux image: /boot/vmlinuz-2.6.32-28-generic-pae Found initrd image: /boot/initrd.img-2.6.32-28-generic-pae Found linux image: /boot/vmlinuz-2.6.32-27-generic-pae Found initrd image: /boot/initrd.img-2.6.32-27-generic-pae Found memtest86+ image: /boot/memtest86+.bin Found Microsoft Windows XP Professional on /dev/sdb1 done alan@alan-desktop:~$ 


Will now reboot my system and hope it works !

---

### Post by Geroman21 on 2011-07-20
I rebooted my system but it didnt work, Window's is not listed....

Here is my screenshot:









Regards Alan
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Alan F on 2011-07-20
Have you tried going down past "Memory Test". 

There is something offscreen below it.

---

### Post by Blasphemist on 2011-07-20
First, windows boot is still intact it seems and I do think arrowing down would likely find windows to boot. You have a bunch of old kernels which really isn't an issue and can be addressed in a couple ways. One is to remove the old kernels, being sure to do it right. The other is to change grub to condense them all into one entry, previous versions. 

Here is a post on removing the older kernel versions using synaptic. [http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

Another other option is to use grub customizer. [http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

It sounds like you also want to set the default OS to windows. I think you should refer to this. [http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

### Post by ddastoor on 2011-07-20
Is /dev/sdb1 an external USB drive by any chance ? Or do you have 2 internal hard disks sda1 and sda2 ?

- Dinshaw

---

### Post by ddastoor on 2011-07-20
Or of course, boot into Ubuntu and then check your grub.cfg file (or menu.lst) and then make sure that the following lines are in there:

title Microsoft Windows
root (hd1,0)
savedefault
makeactive
chainloader +1


Note, that (hd1,0) = /dev/sdb1
(hd0,0) = /dev/sda1
etc

---

### Post by Geroman21 on 2011-07-20
Big Thanks for that it worked a treat ! Can now boot into windows !


I will look at re-installing GRUB boot loader, so I dont have to scroll down the list every time I want to load Windows. 




Thanks for your Help, very much appreciated !

Alan

---

### Post by kroq-gar78 on 2011-07-20
can't you just remove some kernels from ubuntu?

```
sudo apt-get remove linux-headers-(kernel version)-pae linux-headers-(kernel version)-pae` linux-image-(kernel version)
```

So, an example would be: 
```
sudo apt-get remove linux-headers-2.6.32-31-generic-pae linux-image-2.6.32-31-generic-pae linux-headers-2.6.32-31
```

and replace the kernel version with whichever version you want to remove. I suggest keeping the 2 newest kernel versions (one because it's new and one in case something funky happens with the previous kernel)

---

### Post by ddastoor on 2011-07-20
> so I dont have to scroll down the list every time I want to load Windows. 


obviously this is grub1, the old version... 

also, u don't have to scroll down.. in ur grub.cfg or menu.lst, have a line that says 

default n

where n = 0 or 1 or 2,... etc.. this is counting the number of entries (starting with title) from top to bottom in ur file.. 0 is the first entry, etc... 

so if ur windows "entry" is 3rd physically from top to bottom in ur grub file, just put 

default 2

hope this helps

---

