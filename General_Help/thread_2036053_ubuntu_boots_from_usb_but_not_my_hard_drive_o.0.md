---
title: "ubuntu boots from usb but not my hard drive? o.0"
date: 2012-08-01
forum: General Help
---

### Post by KIRON127 on 2012-08-01
hey guys, this issue has been driving me crazy for the past 4 days and i cant figure out what to do. i have an i7 2600k, asus p8z68 v-pro/gen3 board, and an nvidia gtx570 in my computer and for like 4 months i couldn't get ubuntu to boot at all until i found out i had to switch to internal graphics and not my 570 so since i passed that hump and got ubuntu to boot from a usb i now can't boot it from a hard drive after a full install. i have a 1tb hard drive with windows and a seperate 120gb i want ubuntu on so i boot from the usb perfectly fine, no problem. then i install ubuntu on the 120gb using a ext4 file system and placing the bootloader (grub) on the same drive. then after the install i reboot, go to bios and select my ubuntu drive (do this with all drives other than my main windows drive) and when i try to boot the drive i just installed ubuntu on, i don't even get grub to show up and all i see is a black screen with a blinking cursor. it doesn't recognize keystrokes and nothing typed is showed on the screen, the only thing that is recognized is ctrl+alt+delete which reboots the computer. i have booted ubuntu on 3 other computers (via a 60gb hard drive with a full install of ubuntu booting through usb) perfectly fine. so can you guys help me out here?

p.s. im trying to run 12.04 64bit

---

### Post by beboylips on 2012-08-01
GRUB installed on your main partition/hard drive. Boot from it. Probably the same partition as your Windows install.

-Beboy

---

### Post by oldfred on 2012-08-01
You may still need nomodeset on first boot. Not sure if then you install nVidia driver and switch to nVidia in BIOS if then that will work?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You should be able to hold shift key down from BIOS to get a grub menu. It normally shows if it has found the other operating systems but must not have yet.

Once booted try this to add Windows to boot menu.
sudo update-grub

If all that does not work, post this to see if it is a grub/boot issue, but I expect it is boot parameters.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

