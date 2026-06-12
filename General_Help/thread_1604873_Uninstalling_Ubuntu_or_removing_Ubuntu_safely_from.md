---
title: "Uninstalling Ubuntu or removing Ubuntu safely from dual boot Laptop"
date: 2010-10-24
forum: General Help
---

### Post by $uraj on 2010-10-24
Hi.. I installed ubuntu 10.10. Previously i used to install inside windows. But last time i was using Live USB. Tried to install from it when i was trying ubuntu without harming the computer. I selected Install alongside other OS. Now, it has created a separate partion and i don't know how to remove Ubuntu!!!!! Don worry, i'll use ubuntu forever bec of its simplicity and security feature :)

But someone guide me how to remove the Ubuntu OS safely from seperate partion without harming the Window :)

---

### Post by Hippytaff on 2010-10-24
you can delete the ubuntu partition with windows partitioning software, and resize the windows...though its always wise to back stuff up because things can go wrong :-)

---

### Post by Quackers on 2010-10-24
You may also need to repair your Windows bootloader with the Windows repair cd.

---

### Post by coldraven on 2010-10-24
How about booting with the Live CD. Select "TRY UBUNTU" this time!
Then run Gparted, it should be under System -> Administration

You will probably see three partitions NTFS, Linux and swap.
Select the partition that has Ubuntu on it, the Windows one will say NTFS file sysytem.

Make sure you have selected the correct one or you will lose your Windows forever!!
Delete it.
Then select the swap partition and delete it.
You should now have a big chunk of unallocated space.
Create a new one to fill all the space and format it to NTFS
Nothing will actually happen until you click on "Apply" at the top of the screen so you can abort the process if you are unsure of anything.
Scary stuff!
Quit everything, shutdown, take out the Live CD and re-boot with your Windows CD and select "Recovery Mode".
After a few minutes you eventually get to a system prompt.
Type ```
fixmbr 
``` then ```
exit
```Remove the CD and re-boot.
Windows will be able to use the partition, maybe a good place to keep all your music there.
You will now have drives C: and E: your CD will probably remain as drive D:
Good luck

---

### Post by MrRichard on 2010-10-24
First, boot into Windows, download Easy BCD and install it. With this software, you can restore Window's bootloader to the defaults. Next in Windows, click on the start menu and hover over "Computer." Right click it and go to "manage..." Under Storage->Disk management you can safely delete the Ubuntu partitions.

Hoped this helped :guitar:

---

### Post by $uraj on 2010-10-25
oh.. ok guys.. thanks.. will continue using Ubuntu like this as it responds still faster, boots still faster than it did it when installed inside windows.. Anybody knows how to change the default OS during startup ?? i mean bootup time ?? Now linux loads by default if no key is pressed for 10secs. How to change it to Windows 7 ?? Windows 7 is the 6th choice in the Grub selection list.. Linux is the first entry..

---

### Post by $uraj on 2010-10-25
jus checked Easy BCD site.. can v edit it using that software ??

---

### Post by Hippytaff on 2010-10-25
you can do it in ubuntu using this file /boot/grub/grub.cfg

this is a good place to read up on it :-)
[https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg](https://help.ubuntu.com/community/Grub2#/boot/grub/grub.cfg)

---

