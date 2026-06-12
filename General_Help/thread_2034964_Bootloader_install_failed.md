---
title: "Bootloader install failed"
date: 2012-07-29
forum: General Help
---

### Post by sombranegra79 on 2012-07-29
I'm dualbooting Xubuntu 12.04 LTS alongside Windows 7 on a Sony Vaio VGN-NW15G. When I got to the end of the installation, I got an error message saying "bootloader install failed" and asking me if I wanted to install the bootloader in a different location, giving me the options sda1, sda2 and sda5 (I am not an expert by any means and have no idea what these mean). None of these worked so the only options I had were to install it without a bootloader or abort the installation.

I chose to install it without a bootloader, and now I have no idea how to install it manually. I can boot Windows 7 but can't boot up Xubuntu. Could someone please help me out? And please keep it as simple and as clear as possible - I've read answers to other people who've had the same problem and frankly didn't understand a thing.

---

### Post by oldfred on 2012-07-30
Use Ubuntu liveCD and download this app. Instructions on link. It may fix your issue, but it may be better to run the BootInfo and post the link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

You can also download it as a fully bootable liveCD.

---

### Post by sombranegra79 on 2012-08-01
Thanks a lot, though I've since replaced my defective Xubuntu installation with Linux Mint, though, once I figured the bootloader wasn't the only thing missing. No problems with Mint.

---

