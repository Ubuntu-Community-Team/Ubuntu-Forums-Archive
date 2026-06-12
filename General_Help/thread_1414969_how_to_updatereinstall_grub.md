---
title: "how to update/reinstall grub???"
date: 2010-02-24
forum: General Help
---

### Post by Tjampman on 2010-02-24
Hi guys

After I have installed Linux Mint on my computer, grub can only start Mint and Windows, not Ubuntu. I was careless during the installation and formated my boot partion, at least I think that was my mistake.

Is there any easy way to reinstall grub or do I need to go down the terminal route? I am not very experienced, so in that case what should I do?

How can I edit my grub bootloader? what is the configuration file called and where is it saved? I've looked through my boot partition but cannot find it.
On my boot partition I have found a lot of files that says I should not edit them, as they are auto generated.

My Ubuntu version is 9.10, and the grub boot loader that mint intstalled is 1.97, right now I'm using linux mint 8 Helena

Best regards 
Ole


PS. just to make it clear, I have not formated my Ubuntu partitions, I left my / and /home partition untouched, when I install Mint, and those partitions show up fine on my computer.
also, I have only one hard drive, with several partitions one. by the top I of my head, they are 1 for windows, 2 for ubuntu / and /home, 1 for Linux mint, and the /boot partition which is appx 300 MB.

---

### Post by uncle-c on 2010-02-24
If you formatted your Ubuntu boot partition then re-installing grub will make no difference. You won't be able to use Ubuntu because the boot partiton has been deleted.
Can you show the output of fdisk -l . It will show the partition layout of your hard drive. Do you know on which number partitions the Ubuntu and Mint were installed ? You may have to run this command as superuser. Can you also show the output of your Mint menu.lst file. It may be in your /boot/grub directory.

Just reading your edit it looks as if only your Mint menu.lst file needs changing so you can see the Ubuntu 9.10 on the grub menu. Could you also show the output of your ubuntu 9.10 menu.lst file. It will be in the Ubuntu /boot/grub partition or somewhere similar.

---

