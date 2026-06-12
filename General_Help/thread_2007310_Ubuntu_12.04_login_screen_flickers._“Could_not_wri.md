---
title: "Ubuntu 12.04 login screen flickers. “Could not write bytes: broken pipes”"
date: 2012-06-20
forum: General Help
---

### Post by Braynid on 2012-06-20
I use Ubuntu 12.04 x64 with a dual-boot setup.

Yesterday it worked fine but this morning when I attempted to boot it gets to the login screen and then it just flickers, alternating between the login screen and the console showing boot items (mainly Apache, the last one being "Battery status" although it's a desktop) all with [OK] status. The only error that I can see is: "Could not write bytes: broken pipes" on top of the screen.

The only things I can think of that could cause this are:

Yesterday I've installed the updates provided by the Ubuntu system update but I wasn't really paying attention to the packages.

This morning I had a removable hdd plugged in during boot time, which I usually don't have

Yesterday I've installed Dwarven Fortress that requires some x32 libraries so I've installed ia32 using synaptic. As far as I know this shouldn't brake the system but I didn't reboot yesterday so I can't be sure.

I've tried booting in recovery mode and tried running the utils there but still no luck.

All partitions have plenty of free space on them

I've ran out of ideas. Thanks.

---

### Post by bogan on 2012-06-20
Hi!, **Braynid**,

I have been getting the "Could not write bytes: broken pipes" message ever since I upgraded from 11.10 to m12.04 LTS on the day it was released.

It shows, momentarily, with a tty1 login prompt, just before the GUI Log-in screen, and again after selecting shut down or reboot.

It does not seem to affect operation in any way, and I have been unable to locate any log file info related to it.

I had a thread asking about it but got no response, although I did find one other Post reporting the same message.

So my advice is 'do not worry about it'.

As for the other problem, a hang-up after the 'Checking Battery State (OK)' message, is usually a sign of video driver problems; there was probably a Kernal update and the driver needs reinstalling to the new kernal module. 

What video card do you have? and what version driver is installed?

If it is an Nvidia card, Post:```
sudo apt-cache policy nvidia-current
# and in any case:
sudo Lspci -v   # just the paragraph headed "VGA compatible controller"
```Chao!, **bogan.**

---

### Post by Manyette on 2012-06-20
Just a FWIW, Mint 13 gives this same message at shutdown, but only after I had loaded some packages which were not on the install.

---

### Post by Braynid on 2012-06-28
Hey,

I think you are right as I still see the message momentarily during boot-up just as you said.

I have an integrated Intel video chipset and I didn't have any proprietary drivers installed for it.

I might have been an update but I can't really be sure. My solution was to backup my data and just reinstall Ubuntu as I really needed it for work.

Now it all works fine although I still see the above message during the boot sequence.

Thanks for the reply

> **bogan said:**
> Hi!, **Braynid**,

I have been getting the "Could not write bytes: broken pipes" message ever since I upgraded from 11.10 to m12.04 LTS on the day it was released.

It shows, momentarily, with a tty1 login prompt, just before the GUI Log-in screen, and again after selecting shut down or reboot.

It does not seem to affect operation in any way, and I have been unable to locate any log file info related to it.

I had a thread asking about it but got no response, although I did find one other Post reporting the same message.

So my advice is 'do not worry about it'.

As for the other problem, a hang-up after the 'Checking Battery State (OK)' message, is usually a sign of video driver problems; there was probably a Kernal update and the driver needs reinstalling to the new kernal module. 

What video card do you have? and what version driver is installed?

If it is an Nvidia card, Post:```
sudo apt-cache policy nvidia-current
# and in any case:
sudo Lspci -v   # just the paragraph headed "VGA compatible controller"
```Chao!, **bogan.**

---

