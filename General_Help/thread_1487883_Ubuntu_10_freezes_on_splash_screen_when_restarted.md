---
title: "Ubuntu 10 freezes on splash screen when restarted"
date: 2010-05-19
forum: General Help
---

### Post by Stridulent on 2010-05-19
So I have finally successfully triple-booted Snow Leopard, Windows XP, and Ubuntu 10 on an iMac but I have 1 problem:

Whenever I am in Ubuntu and select "Restart," it goes to the splash screen and loads 2 of the dots and then freezes and hangs there forever. If I do "Shutdown," it works properly.

Note: I am using rEFIt as the triple boot loader. GRUB installed on sda3 with Ubuntu. How should I go about resolving this problem? Thanks to anyone that can help.

---

### Post by Stridulent on 2010-05-19
I installed Ubuntu 9.10 as I thought this was a Lucid Lynx problem but the issue is still here in 9.10. I click "Restart" and it just sits on the splash screen. :(

---

### Post by Catharsis on 2010-05-19
Try removing "splash" from the boot parameters. I know in Grub2 it's a line in /etc/default/grub, but I don't know how it works in rEFIt.

---

### Post by Stridulent on 2010-05-20
> **Catharsis said:**
> Try removing "splash" from the boot parameters. I know in Grub2 it's a line in /etc/default/grub, but I don't know how it works in rEFIt.


Thank you for your reply! I took out "quiet splash." I could not find just a "splash" parameter. Anyways, I can't see any effect here. It still freezes on restart. :(

---

### Post by dino99 on 2010-05-20
what you've described is usually a plymouth issue:

sudo dpkg-reconfigure plymouth

or a video driver issue: check system admin hardware driver to see if yours is activated (what is your graphic chipset and driver used ?)

but with your config as you boot with rEFIT, maybe some issue with grub2 (see your logs), you might be able to remove grub2 with synaptic (grub-pc & grub-common)

---

### Post by Stridulent on 2010-05-20
> **dino99 said:**
> what you've described is usually a plymouth issue:

sudo dpkg-reconfigure plymouth

or a video driver issue: check system admin hardware driver to see if yours is activated (what is your graphic chipset and driver used ?)

but with your config as you boot with rEFIT, maybe some issue with grub2 (see your logs), you might be able to remove grub2 with synaptic (grub-pc & grub-common)


Reconfigured plymouth and activated the graphic drivers (nvidia) and no luck. Now the splash screen is slightly larger and only 1 dot turns orange before it freezes.

Removing grub-pc and grub-common did not stop the grub bootloader. It still freezes when I restart but now there are now dots changing lol!

---

### Post by dino99 on 2010-05-20
try to boot with different settings, either:

- recovery system 
- edit the boot line and add video=vesa (remove splash)

---

### Post by Stridulent on 2010-05-20
> **dino99 said:**
> try to boot with different settings, either:

- recovery system 
- edit the boot line and add video=vesa (remove splash)


I really appreciate all your help, dino. Would you mind explaining how to do the second setting? Sorry, I am a bit of a noob with Ubuntu.

---

### Post by Stridulent on 2010-05-20
Could it possibly be because Swap wasn't installed or set up?

---

### Post by Catharsis on 2010-05-20
> **Stridulent said:**
> I really appreciate all your help, dino. Would you mind explaining how to do the second setting? Sorry, I am a bit of a noob with Ubuntu.

Do it the same way you removed "quiet splash", except this time replace that text with "video=vesa".

Just to be clear, is it freezing on the shutdown splash or the subsequent bootup splash?

See if rebooting through the Terminal fixes it too:
```
sudo reboot
```

---

### Post by Stridulent on 2010-05-21
It's on the splash screen immediately after clicking "Restart," NOT the one following the boot up.

In terminal, "sudo reboot" yields the same freezing outcome where it loads 2 dots orange and then freezes before it actually shuts down (the screen shown immediately after the desktop).

---

### Post by Stridulent on 2010-05-21
Ok, so I made the "video=vesa" switch and now I can see what is going on behind the splash screen.

It looks like the following:

> 
Skipping profile in /etc/apparmor.d/disable:  usr.bin.firefox
*Setting sensors limits
[COLOR=DarkOrange]*[COLOR=Black]Speech-dispatcher configured for user sessions
*Starting Common Unix Printing System:  cupsd

fsck from util-linux-ng 2.17.2
/dev/sda3: clean, 148808/9453568 files, 1480213/37809028 blocks
*starting AppArmor profiles      modem-manager:  Loaded plugin Longcheer
modem manager:  Loaded plugin Huawei
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin ZTE
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Nokia
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Sierra
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Generic
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Option High-Speed
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Ericsson MBM
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin AnyData
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Gobi
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Moto C[/COLOR][/COLOR]
[COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Novatel
[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]modem manager:  Loaded plugin Option

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


*Setting sensors limits
[COLOR=DarkOrange]*[/COLOR][/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]PulseAudio configured for per-user sessions
*Enabling additional executable binary formats binfmt-support
*Checking battery state...
[  1221.195892] Restarting system.
[/COLOR][/COLOR]



Then nothing... locks up. Any ideas?

---

### Post by Stridulent on 2010-05-21
Just did the same set up on another iMac and I'm getting the same problem :(

---

### Post by holycow131415 on 2010-05-21
I have the same problem =/

[http://ubuntuforums.org/showthread.php?t=1474326](http://ubuntuforums.org/showthread.php?t=1474326)

---

### Post by Catharsis on 2010-05-21
Alright, some things:

A) Are you removing "quiet splash" every time? With "splash" removed, you shouldn't see the splash screen (purple w/ ubuntu logo and red/white scrolling dots). If you see this after removing "splash" or "quiet splash", then I don't think you actually removed "splash" from your kernel parameters.

B) Since this issue is present in 9.10, it's not a Plymouth issue, since Karmic used usplash not plymouth. Therefore it is probably a kernel bug. Please do as Dino99 suggested and boot into the recovery kernel (recovery mode) and select "boot normally". See if this fixes it.

C) In recovery mode, choose "root shell" (it's at the bottom). Then type "reboot". If this freezes it, then it's definitely a kernel bug.

D) Try booting with "acpi=force" in the kernel parameters.

E) Try booting with "reboot=b" in the kernel parameters.

F) Try upgrading to the mainline kernel:
32-bit:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
```
64-bit:
```
wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
sudo dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb linux-headers-2.6.34-020634_2.6.34-020634_all.deb linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
```

---

