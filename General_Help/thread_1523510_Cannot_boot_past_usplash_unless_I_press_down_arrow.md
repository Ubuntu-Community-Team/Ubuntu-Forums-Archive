---
title: "Cannot boot past usplash unless I press down arrow on keyboard during usplash"
date: 2010-07-03
forum: General Help
---

### Post by Samulus on 2010-07-03
Hello!

Recently I installed Linux Mint LXDE on my older computer and set it up for use with me and my younger brother. All was going pretty well but then I started noticing these occasional crashes where white stripe would appear on a black background. I found out this was a issue related to x lockups on intel graphics. I have intel graphcis, but I thought it would help if I was more precise about the graphics so here is the output of lspci | grep vga.  [HTML] "00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)"[/HTML] I found the page on the Ubuntu Wiki with solutions to the issue.
([https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes))
I started with the Potential PPA packages solution and tried the package 855gm-fix-exp. Sadly it made the situation worse, I couldn't boot into my system anymore! It would load usplash and instead of the pretty LinuxMint usplash screen with the dots and the picture above it, it was replaced with just the text Linux Mint 9 and the dots, after it booted past usplash my monitor displayed a no signal and then entered standby mode like it wasn't being fed a video signal. So then I restarted the computer and held shift to enter the grub2 boot menu. Then I selected the latest kernel in the list and added i915.modeset=1 after quite splash like it also said in the wiki in Workaround A. This allowed me to boot back into Linux Mint. Back in Linux Mint I completely removed in synaptic the packages from the potential ppa solution and ran the command in Workaround A to make the i.915.modeset=1 permanent:```
 echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
```
Then I rebooted to test it. Now only dots were displayed during the usplash process, it booted past usplash and then displayed nosignal like last time. I then rebooted and tried to add the i915.modeset=1 to grub again and booted like that and it didn't work. Then I rebooted and accidentally hit the down arrow on my computer during usplash. That was when usplash turned black and at the top there was a message about a wrong user group that appeared briefly for a few seconds. Then the screen was black for a few more seconds like it was finishing the boot process, then the screen turned white afterwards for a second, then it took me to the login screen. I was able to login and use my computer successfully after that. I rebooted to see if I was able to recreate what happened and I was. I recreated it 4 times now already. Can anyone help me fix this so that I can boot normally without having to press the down arrow every time? Thanks!

EDIT: Update! I managed to solve this issue by myself... I installed startupmanager in synaptic, and then changed my resolution to 1024 x 768 and color quality to 24 bits. This solved the issue for some strange reason so try that anyone who is having a similar issue.

---

