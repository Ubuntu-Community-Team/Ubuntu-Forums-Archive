---
title: "Can't boot Windows after installing Ubuntu...Please Help"
date: 2009-09-19
forum: General Help
---

### Post by marianna09 on 2009-09-19
Hello,

I had Windows 7 on my HP laptop and installed Ubuntu 64bit on the 2nd partition. Ubuntu does not give me the option to boot Windows 7 now. Is thete something I can do to fix it, I need Windows for school but I don't know how to make this work.

Thank You,

Marianna

---

### Post by SlickRick on 2009-09-19
are you sure that you didn't over-write windows. Start up the partition editor under System>Administration and have a look if both  partitions still exist. If yes, then did you install ubuntu on one single partition or have /boot on a separate partition? If not then GRUB shoul've detected windows and give you an option to choose either OS.
Check the /boot/grub/menu.lst file and see if windows is actually listed, if not then you might have to add it yourself

btw, welcome to the forums

---

### Post by marianna09 on 2009-09-19
> **SlickRick said:**
> are you sure that you didn't over-write windows. Start up the partition editor under System>Administration and have a look if both  partitions still exist. 
If yes, then did you install ubuntu on one single partition or have /boot on a separate partition? If not then GRUB shoul've detected windows and give you an option to choose either OS.
Check the /boot/grub/menu.lst file and see if windows is actually listed, if not then you might have to add it yourself

btw, welcome to the forums

Thank you for replying so quickly 

Yes, it's still there...tried editing menu.lst in with the instructions from this guide:

&#8220;sudo gedit /boot/grub/menu.lst&#8221;

A large text file will open and at the bottom leave a line and add this:
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)[INDENT] [I]title        windows 7 beta (Loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1
[/I][/INDENT]but didn't work (Windows7 does show up in the bootloader now, just wont boot)
[B]
Thank you[/B]

[B]I will attach a gparted screenshot and current menu.lst
(and paste menu.lst below)

[/B]title        Windows 7
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

__________________
I will try adding (Loader) to it and see if that might be it

---

### Post by arrange on 2009-09-19
Should be (hd0,**0**), NOT (hd0,**1**). :)

---

### Post by marianna09 on 2009-09-19
Ok, i'll try that...Thank You!

So here is what I'm trying:

[INDENT][INDENT] title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        f8fa0b6e-d541-4514-b42e-43beb1505195
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f8fa0b6e-d541-4514-b42e-43beb1505195 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        f8fa0b6e-d541-4514-b42e-43beb1505195
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=f8fa0b6e-d541-4514-b42e-43beb1505195 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f8fa0b6e-d541-4514-b42e-43beb1505195
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f8fa0b6e-d541-4514-b42e-43beb1505195 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f8fa0b6e-d541-4514-b42e-43beb1505195
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f8fa0b6e-d541-4514-b42e-43beb1505195 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f8fa0b6e-d541-4514-b42e-43beb1505195
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows 7
[COLOR=Red]rootnoverify    (hd0,0)[/COLOR]
savedefault
makeactive
chainloader    +1[/INDENT][/INDENT]

---

### Post by angryfirelord on 2009-09-19
Try setting the boot flag on your windows partion (/dev/sda1). 

If it doesn't work, what's the Grub error that's returned when you try to boot Windows?

---

### Post by marianna09 on 2009-09-19
> **angryfirelord said:**
> Try setting the boot flag on your windows partion (/dev/sda1). 

If it doesn't work, what's the Grub error that's returned when you try to boot Windows?
Okay...I just changed the menu.lst (0,0 )and saved it but haven't rebooted it...do I do the boot flag too or just the boot flag w/out changing the menu?

and do I edit the boot flag in gparted or somewhere else?
________________________________________________________

I got boot error 12  when I rebooted with the menu I uploaded in the original post, But now I'm afraid to reboot now after changing menu.lst to (0,0) because Ubuntu booted with (0,1) just fine....I just want windows to work not make it the default.
_________________________________________________________
I'll try rebooting anyway...then change the boot flag

---

### Post by marianna09 on 2009-09-19
Wahoooo!

Thank You Arrange!!!

Changing it to (0,0) worked...Thanks So Much!

Out of curiosity...Did that work because it's a chainloader +1 and sda1=0+1?

Thanks again you guys for taking the time to help me...You Rock!

---

### Post by arrange on 2009-09-19
> **marianna09 said:**
> 
Out of curiosity...Did that work because it's a chainloader +1 and sda1=0+1?

No :)

The Grub you're using starts counting from 0, not from 1, so sda1=(hd0,0), sdc5=(hd2,4) etc.

---

### Post by marianna09 on 2009-09-19
> **arrange said:**
> No :)

The Grub you're using starts counting from 0, not from 1, so sda1=(hd0,0), sdc5=(hd2,4) etc.

Thanks...so counts from 0 on both partitions and disks, interesting. Those grub folks like to do things differently I guess...lol

Thank you!
Take Care ;-)

---

### Post by pcjunkie on 2009-09-20
Actually 0 is the default for all computers. Windows likes to be fancy...

In any language anything starts at 0

Array 0 => Item1 1=>item2

So Grub is just viewing the drives as drive array. count drives ++ (count 0 + 1 )

0 = 1
1 = 2

---

