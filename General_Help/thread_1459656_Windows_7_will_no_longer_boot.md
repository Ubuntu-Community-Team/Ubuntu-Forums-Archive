---
title: "Windows 7 will no longer boot"
date: 2010-04-21
forum: General Help
---

### Post by Red_Armada on 2010-04-21
Hello all, I am new to the forum and to Ubuntu is general. I am having issues after installing Ubuntu (64bit) as a dual boot. I have windows 7 installed on a RAID 0 array (2x 500GB) and I recently installed a third HDD (Hitachi 1TB) so I could dual boot Ubuntu without having to patrician my RAID Array. During the install (and I believe this is where I made my mistake) I was given two options 1) to format a drive and install Ubuntu (and this gave me the option of either the RAID array, or the Hitachi drive)and 2) patrician the RAID array with the Windows installation. I selected the first option and the Hitachi drive. 

After installation Ubuntu was running well, but upon restarting the computer it doesn't give me a bootloader, it just boots into Ubuntu. I was worried that it had formatted my RAID array as well as the new drive, but under computer in Ubuntu it shows the filesystem as just under 1TB. I then booted from my Windows DVD, and it recognizes a previous windows installation, however even after removing the new Hitachi drive I am still unable to boot into windows it gives the following error:

GRUB loading.
error: no such disk
grub rescue>

any help would be greatly appreciated, thanks in advance.

---

### Post by oldfred on 2010-04-21
Welcome to the forums.

I do not know raid, but lets document your system, so we know what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Red_Armada on 2010-04-21
Thanks for the reply, I'm afraid I am not entirely sure how to use code tags, or where to place them, I have attached the file you requested however.

---

### Post by oldfred on 2010-04-22
I do not see anything wrong, but grub did install to sda and your Ubuntu is on sdc. If you have set your BIOS to boot sdc you get the errors you are seeing. You could try booting sda, I do not know if that works the same with raid or not.

I would reinstall grub2 to sdc and set boot sdc in BIOS.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by la3875 on 2010-04-22
It seems to me you will have to edit grub to allow you the dual boot option. I think what you have is similar to a dual boot with dual drives and I ran that set up for several years on the family shared computer.

Take a look at this site - [http://members.iinet.net.au/~herman546/p14.html](http://members.iinet.net.au/~herman546/p14.html) Herman's site has been invaluable to my Ubuntu experience.

Your Windows install should still be there unharmed. If you cannot select that disk at start up via boot selection, you might try unplugging the Ubuntu installed drive. Your computer should find the windows install and boot normally.

Keep us posted and be patient. Welcome to Ubuntu!

---

### Post by Red_Armada on 2010-04-22
Thanks for the reply.
So far as I can tell my windows install is still intact. I had already tried removing the drive with the Ubuntu install, however it gave me the: 
GRUB loading.
error: no such disk
grub rescue>
I also ran startup repair from my windows 7 disk, but it wasn't able to find any problems. It's as if the Ubuntu install put a small piece of code on the RAID that prevents me from booting. Thanks for the link, I'll see if I can find anything there.

---

### Post by oldfred on 2010-04-22
The grub error message is because grub was in sda and with sdc uninstalled it could not find the rest of grub in sdc. If you ran the windows repair you probably overwrote the grub in sda but should then boot windows directly. Install grub to sdc and change BIOS to boot sdc.

Another user with similar raid and dual boot. He had old grub.
[http://ubuntuforums.org/showthread.php?t=1457222](http://ubuntuforums.org/showthread.php?t=1457222)

---

### Post by Red_Armada on 2010-04-22
@olffred, I tried restoring the bootloader and it appeared to work fine in the terminal, however I still don't get a bootloader on startup. I only get that Grub error when I physically disconnect the SATA data cable from the Ubuntu HDD. When that drive is attached, Ubuntu boots without issue. What I don't understand, is even after physically disconnecting the Ubuntu drive, and setting the BIOS to boot from my RAID array (which still contains windows) I cannot boot into windows. I ran sudo update-grub and was given this:

Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin

I'm afraid the above is greek to me, thanks again for your help

---

### Post by john newbuntu on 2010-04-22
Set bios to boot from CD and first repair the MBR on your raid array by following:
[http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)

You then have to change your bios to boot from sdc (third drive-hitachi) and not your raid array.  Then boot into ubuntu and run "sudo update-grub2"  from a terminal

---

### Post by oldfred on 2010-04-22
The grub in sda overwrote the windows boot loader in sda. The boot script was not able to totally process the raid array so it did not see your windows install. If your windows is still there you should run the windows repairs per john newbuntu.

---

### Post by Red_Armada on 2010-04-22
@newbuntu, I tried to fix the MBR, unfortunately that didn't solve the problem. I used the Windows 7 disk to find all the patricians, and it appears as if Ubuntu had formed a small patrician on my RAID array (this I believe was stopping windows from booting.) I formatted that patrician (it was about 100mb) and reinstalled Windows on the RAID array (just for good measures). One of the nice feature of Windows 7 is it places all my old files in a windows.old folder on my C drive, so I didn't have to move all my data back from a slow USB external. This seems to have salved the problem and everything is working well,thank you all for your quick responses, your help was greatly appreciated :)

---

### Post by oldfred on 2010-04-22
Windows 7 creates a 100mb boot partition and then puts the rest of the install into the main partition. Some how your win boot must have been messed up. Win repair usually fixes it but if the 100mb is gone it will fix the main partition if that had the boot flag.

As long as it works that is what counts.

---

### Post by Red_Armada on 2010-04-22
@oldfred, That makes sense and everything is working great, all of my data is intact. Thanks again for your help.

---

