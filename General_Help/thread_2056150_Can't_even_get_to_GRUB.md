---
title: "Can't even get to GRUB"
date: 2012-09-10
forum: General Help
---

### Post by modernwatchmaker on 2012-09-10
I've got an Acer laptop with a fairly recent but not new distro of Ubuntu on it, probably Lucid or Maverick. I used a USB stick for the installation. Somehow the laptop got messed up and wouldn't boot without the USB stick plugged in.

Now comes the fun part. I don't have the USB stick anymore, and because of this cannot get past the manufacturer boot screen. I can press <F2> for a menu but no matter how I arrange the boot sequence I can't seem to get the computer to run. Even if I put a boot CD into the drive I can't get it to boot into the CD.

I'd be glad to start from scratch with a fresh install but I can't for the life of me figure out how. Where would I start? What terms would I even Google?

---

### Post by opensshd on 2012-09-10
Have you tried an alternate usb boot? Perhaps your cd/dvd is going?

---

### Post by opensshd on 2012-09-10
Or perhaps whatever whacky setup that required a usb key to boot needs to be purged. I would reset BIOS to default settings (perhaps update/reload BIOS) then reinstall a boot manager that will update the disk MBR.

---

### Post by oldfred on 2012-09-10
You can download this into an Ubuntu liveCD or USB or download as a full repairCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by dcstar on 2012-09-11
> **modernwatchmaker said:**
> 
..........
I'd be glad to start from scratch with a fresh install but I can't for the life of me figure out how. Where would I start? What terms would I even Google?

Simplest way is to remove the drive and reformat (write a new partition table) it in another machine or external drive enclosure.

If you want to leave it in the laptop and get adventurous you can change the BIOS settings for the drive to a crazy geometry, then boot up and format it with a Live CD, go back into the BIOS and set it back to normal and you should then be able to install as if it is a fresh drive.

---

### Post by modernwatchmaker on 2012-09-28
Thanks... If I could get a live CD to run I totally would, but that's not the case unfortunately.

Ideally I'd like to fix this within the laptop.

> If you want to leave it in the laptop and get adventurous you can change the BIOS settings for the drive to a crazy geometry...

I'm not quite sure what you mean. I've gone through every boot order possible with the laptop and still can't get a live CD to run. I get past the boot splash and then the eternal blinking underscore.

---

### Post by oldfred on 2012-09-28
If you hold shift key from BIOS splash do you get to a menu?

---

