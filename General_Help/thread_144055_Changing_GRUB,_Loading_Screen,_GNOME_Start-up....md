---
title: "Changing GRUB, Loading Screen, GNOME Start-up..."
date: 2006-03-13
forum: General Help
---

### Post by th3gh05t on 2006-03-13
Hi, 

I am fairly new to Ubuntu and I was wondering how I go about changing the GRUB bootloader screen. (The one where you select what OS to boot to.)

Is there a program that is similar to the "Login Screen" for changing the GRUB?

I was also wondering how to change the screen where it shows all of the processes starting. (On my computer, there is small brown font, and a big gray bar at the bottom.)

Also, how do I change the brown Ubuntu screen when it is loading GNOME?

I have searched around gnome-look.org but couldn't find anything for any of these.

Any links or insight will be greatly appreciated.

Thanks for your time! 

th3gh05t

---

### Post by Steve1961 on 2006-03-13
This link might help with changing the default boot screen image:

[http://www.zwhlug.nl/content/grub_the_boot_splash_image_howto](http://www.zwhlug.nl/content/grub_the_boot_splash_image_howto)

As for the bootsplash screen, as far as I know the only way to change this would be to recompile your kernel and add your own patch - although not sure about this.

---

### Post by Jawbreaker4Fs on 2006-03-13
You might want to check out [this Howto]("http://www.ubuntuforums.org/showthread.php?t=82835"). Although you're right Steve, it didn't go through until I recompiled the kernel.

---

### Post by ComplexNumber on 2006-03-13
there's also some themes available form gnome-look together weith pics of how it looks:

einstein - [http://www.gnome-look.org/content/show.php?content=35703]("http://www.gnome-look.org/content/show.php?content=35703")
[FONT=Arial]
che gueravara - [http://www.gnome-look.org/content/show.php?content=35754]("http://www.gnome-look.org/content/show.php?content=35754")
[/FONT]

---

### Post by th3gh05t on 2006-03-13
[QUOTE=Steve1961]This link might help with changing the default boot screen image:

[http://www.zwhlug.nl/content/grub_the_boot_splash_image_howto](http://www.zwhlug.nl/content/grub_the_boot_splash_image_howto)

As for the bootsplash screen, as far as I know the only way to change this would be to recompile your kernel and add your own patch - although not sure about this.[/QUOTE]

Hi, 

Thanks for your reply! 

Not wanting to mess up my menu.1st file, I wanted to ask the question here first.

> The tricky part probably is figuring out where your .xpm file is located. My /boot is a seperate partition which is /dev/hda1 and that translates to hd0,0. If you would only have one partition (example: /dev/hdb3) and /boot would be located on that, it would translate to hd1,2 and you would have to use (hd1,2)/boot/grub/your-splashimage.xpm to your menu.lst

I have a total of three partitions, 1 for Ubuntu, and the other 2 are for Win XP.

**Partition 1:**
Device: /dev/hda1
Access path: /media/hda1
Filesystem: Windows NTFS

**Partition 5:**
Device: /dev/hda5
Access Path: /media/hda5
Filesystem: Windows NTFS

**Partition 3:**
Device: /dev/hda3
Access Path: /
Filesystem: Extended 3

What values do I put in for the hd?

*splashimage=(hd0,0)/grub/your-splashimage.xpm*

Thanks again!

---

### Post by Xian on 2006-03-13
[QUOTE=th3gh05t]What values do I put in for the hd?

*splashimage=(hd0,0)/grub/your-splashimage.xpm*
[/QUOTE]

You list your linux partition at /dev/hda3 so you would need:

splashimage=(hd0,2)/grub/your-splashimage.xpm

---

