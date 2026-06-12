---
title: "Removing Ubuntu"
date: 2010-03-25
forum: General Help
---

### Post by rhrodd on 2010-03-25
As a long time Windows user, I recently decided to give Ubuntu a try. As I live in a part of the world where I have to use a Vodacom GPRS (not even 3G) connection using a Vodafone E-220 USB modem, I sent for a disk and excitedly installed it on my Window7 PC when 9.04 arrived. However it will not connect to the internet, even though it recognises the E220 and I am using correct number, etc. Went to the support forum, and all I can find is people stating they have same problem with 9.04 - a few suggested some work arounds ( not that it helps a newby Ubuntu user!) As I cannot get an internet connection that works, I guess I will have to stay with Windows, BUT how do I uninstall Ubuntu - first time I have found a program that does not have an uninstall option

---

### Post by new_tolinux on 2010-03-25
Maybe you should try 9.10. My experience is that some GPRS-products do work there, but not in 9.04.

Are you using wubi or did you install it on a separate partition. If you installed it on a separate partition you can just install Windows (or another OS) and delete the ubuntu-partitions during installation.

As for wubi: I have no idea how to uninstall then.

---

### Post by rhrodd on 2010-03-25
Sorry - said I was a newby - I actually have installed 9.10!  I installed it side by side using the Ubuntu disk. Windows still works - thank goodness!

---

### Post by Gemnoc on 2010-03-25
> **new_tolinux said:**
> As for wubi: I have no idea how to uninstall then.
If the Ubuntu installation was made with wubi (the Ubuntu installer in Windows), it's really easy: in Windows, go to Control Panel > Add/remove programs, and uninstall Ubuntu right there, it takes about 5 seconds.

But we need to know for sure how rhrodd installed Ubuntu in the first place.

---

### Post by Gemnoc on 2010-03-25
> **rhrodd said:**
> I installed it side by side using the Ubuntu disk. Windows still works - thank goodness!
Just to be clear.

Did you start your computer on the LiveCD demo then proceeded with installation? (first choice on the LiveCD, changing the boot order in the BIOS to start on the CD-Rom drive is necessary)

Or did you install in Windows (second option on the LiveCD, also called "wubi" install)?

---

### Post by rhrodd on 2010-03-25
Thanks for all the interest! I had Windows 7 on PC, Placed the Ubuntu disk in as I restarted PC, and it booted using the CD. I chose the option to install Ubuntu, and it was installed on a new partition on the disk. When PC starts have option which OS to use. Hope this helps!

---

### Post by Gemnoc on 2010-03-25
No problem. *(Maybe the next Ubuntu release will recognize your internet setup. But I recommend that you try the LiveCD in demo mode next time. If it's unable to connect to the internet, you'll know not to install it again.)*

So we've pin pointed your method of installation.

This method of installation installs Grub-pc onto your disk. Grub is a boot loader and manager that gives you the choice to load either Ubuntu or Windows 7.

Unfortunately, I know the general principles, but not the exact steps. You need to uninstall Grub-pc, then restore Windows 7's bootloader. Finally, you'll be able to delete the Ubuntu partition in the Windows "partition utility" (don't remember the name) which can be opened by right-clicking the "My Computer" icon and choosing "Manage". (well at least that's the way to do it in XP, not sure for Win7)

I have found this tutorial on [=General%20Tips"]how to restore Windows 7 Master Boot Record]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[2).

Let's hope somebody else chimes in to complete the info I gave you.

Good luck!

P.S. Found this other how-to that seems complete:
[http://www.sevenforums.com/installation-setup/62209-remove-grub-restore-windows-7-a.html](http://www.sevenforums.com/installation-setup/62209-remove-grub-restore-windows-7-a.html)

It appears that there is no need to uninstall Grub-pc, as it is erased by restoring Win7 MBR.

---

### Post by Irony on 2010-03-25
Try this;

[http://www.youtube.com/watch?v=ICV5dxlgbTM](http://www.youtube.com/watch?v=ICV5dxlgbTM)
[http://kb.acronis.com/content/1507](http://kb.acronis.com/content/1507)

i.e. Just restore your windows bootloader. Once you are back into windows you can go to Admin tools and format your Ubuntu partition as ntfs and use it to store stuff.

---

### Post by Paddy Landau on 2010-03-25
Just to explain a little more...

Ubuntu doesn't have an uninstall option, just as Windows doesn't have an uninstall option, because it's not a program; it's an operating system.

Ubuntu would have split your disk into three pieces, called "partitions". The first partition will have Windows. (Actually, depending on your manufacturer, there may be more than one for Windows.)

The subsequent partitions will be Ubuntu ("ext4") and something called "swap", possibly inside yet another partition called "Extended". (This is how modern hard disks work.)

When you have fixed your Windows MBR, you will want to reclaim the space from the partitions that Ubuntu took. Windows 7 will have some type of partition manager (sorry, I don't know Windows 7; you'll have to ask Windows support for how to use it). This will let you find and delete the Ubuntu partitions (ext4 and swap, and possibly Extended).

When you do this, be VERY CAREFUL to delete the Ubuntu partitions and not your Windows ones! Because we don't know the exact structure of your partitions, we can't give you specific advice. Again, your Windows support can lead you through this.

After they've been deleted, then you grow your Windows partition into the freed space.

It is possible to do all this through Ubuntu's Live CD, although the final step -- growing Windows 7 -- should be done with Windows and not with Ubuntu. If you would like to do it this way, ask here and we'll give you the right help.

---

### Post by Gemnoc on 2010-03-25
Nicely explained, Paddy Landau. :)

I think with my second link, he should be set.

---

### Post by rhrodd on 2010-03-25
Thanks to everyone for the help - I can't help but feel very bad to have to stop using Ubuntu with all the support you all have provided!
 
 Maybe I should keep it on the PC, get familiar with it and hope the GPRS problem is solved soon, and the fix is easy enough for me to make! As a retired person, I would really like to be able to stop supporting Microsoft! Ubuntu seems a far better option - if only the damn modem would work!!
 
Thanks again people

---

### Post by Paddy Landau on 2010-03-26
> **rhrodd said:**
> I can't help but feel very bad to have to stop using Ubuntu with all the support you all have provided!
Don't feel bad... It's only an operating system!

There is one more thing that hadn't occurred to me. If the driver works under Windows, it may be possible to get that driver to work under Linux using ndiswrapper. Ndiswrapper gets Windows modem drivers to work under Linux.

It's been so long since I've used it that I don't remember how. You can look up how in the [ndiswrapper community documentation]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"), search these forums, and ask if you get stuck.

---

