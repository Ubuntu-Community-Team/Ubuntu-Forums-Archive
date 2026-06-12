---
title: "After update elementary (ubuntu 10.10) won't boot"
date: 2011-10-19
forum: General Help
---

### Post by ywatson on 2011-10-19
Hi,

This morning I installed a few updates from the Update Manager, and when I restarted my computer the screen went black (even without cursor) by the time it should have showed the login-screen and it wouldn't respond anymore.

From the var/log/apt/history.log I got a list of the updates that I installed I belief:

```
Start-Date: 2011-10-19  10:25:49
Upgrade: libkrb5-3:amd64 (1.8.1+dfsg-5ubuntu0.7, 1.8.1+dfsg-5ubuntu0.8), libk5crypto3:amd64 (1.8.1+dfsg-5ubuntu0.7, 1.8.1+dfsg-5ubuntu0.8), xserver-xorg-core:amd64 (1.9.0-0ubuntu7.3, 1.9.0-0ubuntu7.5), xserver-common:amd64 (1.9.0-0ubuntu7.3, 1.9.0-0ubuntu7.5), libkrb5support0:amd64 (1.8.1+dfsg-5ubuntu0.7, 1.8.1+dfsg-5ubuntu0.8), libgssapi-krb5-2:amd64 (1.8.1+dfsg-5ubuntu0.7, 1.8.1+dfsg-5ubuntu0.8)
End-Date: 2011-10-19  10:25:52
```

By searching on the web I found out that it probably has something to do with the xserver-updates and my graphics card. But before I realised that I tried Boot-Repair to fix GRUB, which I thought could be the problem. After that I got the Grub-menu when I booted (normally it would just go directly to the login-screen), with two kernel-versions. Choosing the latest would bring me back to the black screen. The earlier version I never tried and now I can't get there anymore.

I tried a few little things, nothing critical I think and I don't remember all of it (i.a. tried a Super Grub Disk iso on an usb flash drive with unetbootin, but it wouldn't even boot), later I ran Boot-Repair for the second time and now it gave an error about MBR (even though I don't have dual boot!) and apparently it did something like repairing MBR too. Booting after that gave me another issue: it doesn't even get to the GRUB-menu anymore, it loads a long time and then shows the following message:

```
Realtek PCIe GBE Family Controller Series v2.38 (12/24/10)

CLIENT MAC ADDR: (long number) GUID: (even longer number)
PXE-E53: No boot filename received

PXE-M0F: Exiting PXE ROM.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key...
```

Anyone any ideas what the issue is or what to try?
This is my only computer so it's very frustrating not being able to boot...

Thanks!

---

### Post by bibble235 on 2011-10-19
Sound more like you have changed your boot sequence in the bios. Looks like you are trying to boot from the network.

---

### Post by ywatson on 2011-10-19
You were right, it was trying to boot from the network. I haven't changed anything in the booting order though. Apparently that was the fourth boot option, and the first three didn't work (CD/DVD, Hard Drive, External Harddrive). I disabled the fourth, now I only get the last part of the message on a black screen:

```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key...
```

So I guess GRUB isn't recognized on the harddrive?

---

### Post by effenberg0x0 on 2011-10-19
> **ywatson said:**
> You were right, it was trying to boot from the network. I haven't changed anything in the booting order though. Apparently that was the fourth boot option, and the first three didn't work (CD/DVD, Hard Drive, External Harddrive). I disabled the fourth, now I only get the last part of the message on a black screen:

```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key...
```So I guess GRUB isn't recognized on the harddrive?

You have the option to select valid boot devices in your BIOS, activate and deactivate them, and set their order. Since you probably won't ever boot from the network, you can disable it. Normally, it is safer to have the system look on CD, USB and the main HDD, in this order. Also, many motherboards allow you to press a key (generally F12) when the PC boots to select boot device. 

You have to check if your PC is not trying to boot from a CD with no OS, from a USB with no OS, or even from other devices connected to the PC. Maybe you have more than one HDD, or even a external one, and the BIOS is looking for a OS in it.

If you're absolutely sure that the BIOS is set to look for a OS in your main HDD, in which Ubuntu is installed, and you still get that message, you might have uninstalled or corrupted the MBR (Master Boot Record).

The MBR is written to the first sectors of the HDD. BIOS always look for those sectors. Grub should be there. This is how booting a OS works. 

Use grub-repair according to the instructions in here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You have to make sure that your HDD has a MBR with grub installed in it. And that the partition booted by this MBR is the one with your OS (Ubuntu, WIndows, don't know what you have there).

---

### Post by ywatson on 2011-10-19
Thanks for the advice. I'm back at the first issue because I was able to get the GRUB-menu back through a now working Super Grub Disk on a pendrive.

Choosing the earlier kernel version now doesn't make a difference, I get the same black screen and no response.

The only option working in de Super Grub Disk menu was "(ROOT) !LINUX! (>=2)  MANUAL", which brought me eventually to the "Recovery Menu" (where you come when you choose Recovery Mode in the GRUB-menu):

"Repair broken packages" - done, no problems there
"Update grub bootloader" - also done, again: went well
"failsafeX" - won't start, the menu stays, when I choose it nothing happens...
"Resume normal boot" - here it goes further than it went when choosing one of both kernel versions in the GRUB-menu, so it does seem to indicate that there is a working GRUB, but than it hangs at:

```
Ubuntu 10.10 me-home tty1

me-home login: _
```


Well I have one SSD in my computer and one external HDD. I'm only running elementary OS Jupiter (which is based on the core of Ubuntu 10.10).

---

### Post by bibble235 on 2011-10-19
probably because your graphics card does not work with Ubuntu. Do you know the brand? Once you find that out find the driver and reinstall.

at login use you normal login to get to the command line

sudo bash

type your password again. Then use apt-get install <package> to install your video drivers. I are struggling just let me know the video card and I will have a look

---

### Post by ywatson on 2011-10-20
My graphics card is a Sapphire HD 6850, I will try to find the right driver and reinstall it as you suggest. I also found out that maybe just resetting my xorg.conf file to default is enough to get it working again:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Will try that first and let you know how it goes.

---

### Post by ywatson on 2011-10-20
Found a solution!

First, resetting the xorg.conf file to default didn't changed anything. Then I went searching for a driver, but saw a similar new post right under this one: [http://ubuntuforums.org/showthread.php?t=1865066](http://ubuntuforums.org/showthread.php?t=1865066)

There I found the following command to get the right driver:

```
sudo apt-get install fglrx
```It supports a lot of ATI graphics cards ([http://en.wikipedia.org/wiki/AMD_Catalyst#Supported_products](http://en.wikipedia.org/wiki/AMD_Catalyst#Supported_products)). 

This gave me the possibility to login again, only with the known "AMD unsupported hardware"-watermark issue, so I then tried to install my old (I belief open-source) driver which I had stored somewhere (ati-driver-installer-11-6-x86.x86_64.run) and which just worked again without the watermark and with the new updates.

Thank you for your help, it's great to get some support when your trying many things without getting it to work. :)

---

