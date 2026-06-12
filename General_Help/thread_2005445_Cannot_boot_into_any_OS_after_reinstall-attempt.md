---
title: "Cannot boot into any OS after reinstall-attempt"
date: 2012-06-17
forum: General Help
---

### Post by Inorien on 2012-06-17
Hello

I'll outline first the introduction:
I installed Linux on a separate partition on my Toshiba laptop alongside Windows 7 (64bit machine), from a USB stick install. After some initial tomfoolery I managed to get the two OS's working, so that upon booting the machine I was able to choose either OS and it would work without any errors.

Then disaster struck - I decided that after too much initial messing around on Ubuntu, it was time to reinstall it and go for a fresh start with me knowing a bit more what I was doing this time. I followed the instructions [here ]("https://sites.google.com/site/easylinuxtipsproject/reinstallation")to reinstall, except in this case I was using a USB stick (the same prodigal USB stick mentioned above) instead of a Live CD. I found GParter and "destroyed" (as the page so aptly put it) the Ubuntu partitions, then rebooted the laptop (step 3). Here is where everything went wrong - first, GRUB was no longer showing up. I expected this seeing as I had deleted the Ubuntu partitions. Then, something even worse happened - I got an error message stating the following:

error: no such device: 55922e26-cce3-4a44-8788-dbc92710ae51
grub rescue>

This was bad. I rebooted the system in a panic and tried to boot from the HDD in an attempt to get to Windows. Then I got this:

error: no such partition.
grub rescue>

I rebooted again, backing out and trying all kinds of funky combinations booting from USB or HDD - same results every time. I decided to try a Live CD from my desktop computer (didn't have any luck with this during original installation, but worth a shot). I made it by burning the ISO image to the disk (not the actual .iso file, but the contents of it). This happened:

error: no such partition.
grub rescue>

I have no idea where to go from here. Booting from USB, CD or HDD doesn't bring me any joy, all I can access is the BIOS setup. Any and all help would be much appreciated!

-Ino

---

### Post by drs305 on 2012-06-17
The partition GRUB is looking for no longer exists, which is why you are getting the grub rescue prompt.

No worries. If the Windows boot files are intact and the boot flag is still on the correct Windows partition (Ubuntu doesn't use it so it shouldn't have changed) we can restore the Windows bootloader.

Boot your LiveUSB to the Ubuntu desktop. Install and set up lilo by running the commands. Disregard the messages saying you need to run further instructions; just run the following 2 commands and reboot. Hopefully you will see your Windows bootloader.

Assuming your BIOS boots drive sda and that is where Windows resides:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by Inorien on 2012-06-17
Thanks for the fast reply, drs305 - I'm unable to boot to the desktop using the LiveUSB. It gives me the "error: no such device" error as shown in my OP.

---

### Post by WorMzy on 2012-06-17
Then you're doing it wrong. Your LiveUSB shouldn't be using the same partition that your borked grub is trying to use. Make sure you're booting from the USB drive by checking your settings in your BIOS and/or making sure you're booting the right device from the boot menu.

---

### Post by Inorien on 2012-06-17
> **WorMzy said:**
> Then you're doing it wrong. Your LiveUSB shouldn't be using the same partition that your borked grub is trying to use. Make sure you're booting from the USB drive by checking your settings in your BIOS and/or making sure you're booting the right device from the boot menu.

I am very sure I'm doing it right! USB sitting in the USB slot (tried on all 4 slots on my laptop), booting, Pressing F12 at the TOSHIBA splash screen, it gives me options to boot from HDD, CD Drive, LAN or USB. I tell it to do USB and it gives me that.

EDIT: I'm reformatting and recreating the original LiveUSB, will report back soon.

---

### Post by drs305 on 2012-06-17
Can you boot to a linux OS via any method? USB, LiveCD, rescue cd, rescue usb? If you can get to a linux terminal with an internet connection or capability of running lilo you can follow my instructions.

---

### Post by Inorien on 2012-06-17
After fighting aliens, I am successfully booted into Ubuntu from a newly made Live USB. Carrying out your orders now, Admiral drs305.

EDIT: Windows loaded and applied about 27000 update operations. It's rebooting now.

---

### Post by Inorien on 2012-06-17
Successfully booted into Windows! Now all that's left to complete the cycle is to install Ubuntu. As far as I'm aware, the original partitions on the disk are just empty unallocated space - am I clear to install Ubuntu over this?

Edit: Sorry for the double post, can hardly concentrate I'm so tired.

Edit: Going ahead with the installation. I read somewhere that Linux will automatically use free space on the disk, I guess that will soon be known, and I'll repeat this little adventure myself if need be. 

Thanks for all the help guys!

---

### Post by WorMzy on 2012-06-17
> I am very sure I'm doing it right!

> **Inorien said:**
> After fighting aliens, I am successfully booted into Ubuntu from a newly made Live USB. Carrying out your orders now, Admiral drs305.

Heh, I like you. :P


> Sorry for the double post, can hardly concentrate I'm so tired.

Then sleep. The problems will still be there in the morning, I assure you. You're more likely to f*** something up if you can't concentrate.

> Going ahead with the installation. I read somewhere that Linux will automatically use free space on the disk, I guess that will soon be known, and I'll repeat this little adventure myself if need be. 

That depends entirely on the distro you're trying to install. I'm using Arch, myself. Attempt to install that when you're not awake and you'll soon find out how unforgiving Linux can be. :P

---

### Post by drs305 on 2012-06-17
Glad you got Windows working. I think we'd all recommend taking your time before installing.

In the off chance you decided to sleep rather than compute, any repartitioning or resizing should be done in Windows. And most of us prefer using the manual installation (3rd option - Do something else) so you can manually choose the partition on which to install Ubuntu.

In any case, we all wish you success.  :P

---

### Post by Inorien on 2012-06-18
Installation completed successfully on the unallocated free space, and I went ahead and installed Grub on sda. Everything is now going harmoniously, just as it was before the mess started.

Thanks again for the help!

@WorMzy
I'm using Ubuntu, I read somewhere that it was a good one to start with. I'll probably move on to something a little more advanced once I stop making silly mistakes like this, hah!

---

