---
title: "Unable to boot into Windows EVEN after using fixmbr, etc."
date: 2009-07-18
forum: General Help
---

### Post by Wally_dog on 2009-07-18
Hey guys. Let's just say after an experiment with PC-BSD, I will likely NEVER use or try a BSD-based operating system again.

So basically, I am at a complete loss as to what I should do here. Here is the problem:

Today I wanted to install PC-BSD after hearing good things about BSD. I went ahead and installed PC-BSD in a dual-boot configuration with Windows 7. Now before, I had an OSx86 dual-boot, so I just wiped OSx86 in favor of PC-BSD. So the install went fine, but then when I try to boot my PC, select Windows from the PC-BSD bootloader, I am brought to the Windows bootloader, which when told to boot Windows 7, cannot boot Windows 7.

My first question is this: HOW is the Windows 7 bootloader still existing on my hard drive????? Shouldn't the PC-BSD bootloader have overwritten it?

So, in an attempt to fix the solution (this always works for me), I popped in the Windows 7 install disc, clicked Repair Installation, then clicked Repair Startup. Everything goes ok. Now, when I reboot, I come to the PC-BSD bootloader. I press Windows 7 again, and it takes me to the Windows 7 bootloader, which STILL CANNOT FIND WINDOWS!!!

Now I am starting to get worried. I do the second method I can think of to get a working operating system and bootloader: install Ubuntu Linux. Ubuntu installs fine, and so does GRUB. So right now, I am using Ubuntu, which I am glad I can do for right now. However, I still want access to Windows. I decided to reboot and see if I could boot Windows. I reboot, and I see an option "Windows Vista (loader)". Now I know that the Windows Vista and 7 loaders are the exact same. So I went ahead and selected Windows Vista (loader). Guess what happens? I GET THE SAME WINDOWS BOOTLOADER. Even better? IT STILL CAN'T BOOT WINDOWS! It tells me it can't find anywhere that Windows is installed, however a quick looksie of my hard drive from Ubuntu verifies that Windows is indeed present.

My second question: Please please please, HOW can I remove the Windows bootloader and make GRUB boot Windows 7? I can only think of one way that would fix the whole mess, but it is a very unfavorable option right now: wipe my hard drive.

So please, I would really like to be able to fix this problem... I have never had this type of problem before when trying to dual-boot. I've tried everything I thought of and even tried everything I've seen on Google that looks feasible.

Thanks for helping

-Mike

---

### Post by master_kernel on 2009-07-18
Download Super GRUB Disc: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Burn it to a CD.

Throw in your Winblows repair disc, run it multiple times until it finds no error, format your MBR, and run the repair again. Boot up, and into Windows. If you want Ubuntu again, put it the SGD, and follow the on-screen directions. Your Windows install should work from GRUB now.

---

### Post by Wally_dog on 2009-07-18
Well thats the thing. GRUB only is able to boot the Windows bootloader. So whenever I run fixmbr or another bootloader fix, it just erases GRUB. But I guess I will just keep trying the Windows repair disc.

Ok, after 4 times with the repair, GRUB is still somehow my bootloader, but it CAN boot Windows. Hooray! But now a new problem has arisen: I can't put any icons on my desktop besides the Recycle Bin. If I drag, let's say the C: drive to make a shortcut onto the desktop, it lets me do that, but the icon won't be there. Now if I go into my actual Desktop folder, the icons are all there. I'm baffled :P Any help here?

---

### Post by moster on 2009-07-19
If fixmbr do not work, try fixboot.

[http://askbobrankin.com/fix_mbr.html]("http://askbobrankin.com/fix_mbr.html")

---

