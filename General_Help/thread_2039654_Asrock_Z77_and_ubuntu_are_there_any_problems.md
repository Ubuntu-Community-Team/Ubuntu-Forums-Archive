---
title: "Asrock Z77 and ubuntu: are there any problems?"
date: 2012-08-09
forum: General Help
---

### Post by erupter on 2012-08-09
Hi guys.
I've got my new supa-dupa rig setup and it's wonderful.
It has the following components
MB: Asrock Z77 Extreme6
CPU: Intel I7 2600
VGA: AMD Radeon 7970
the rest is unimportant.

Fact is that Ubuntu doesn't shutdown.
It gets stuck at the white-logo-on-purple screen and sits there.

Also the loading screen appears not to work good: on starting after boot, it again sits at the white-logo-on-purple without animating.
The animation takes place only for the last split second before loading the login screen.

The additional drivers interface shows two AMD driver releases: one ATI/AMD proprietary FGLRX graphics drivers, and the other the same but with an added *(post-release updates)*.

Now the first time around after installing, I chose the second one but it didn't get through with the update, stating some error.
So I installed the normal one and it appears active.

So it may be a vga thing, but it could also be a motherboard thing; and this is my suspect also because with this new EFI bioes around I had some problems installing Ubuntu: booting from the USB drive I made under windows, I had the choice of just the USB drive, or a kind of EFI-managed usb drive.

With the first the correct Ubuntu live/install menu appeared, but installation failed (don't remember how, did this a month ago), with the EFI-managed one just the GRUB menu appeared but installation went fine.

Anyone has any idea what is happening here?

---

### Post by 2F4U on 2012-08-09
Did you already look into the log files? They may give a hint on what Ubuntu is waiting during shutdown. I would suspect that it is waiting on a hardware component to be shut off and the log files should indicate which component it is.

---

### Post by oldfred on 2012-08-09
Do not know about video.

If dual booting grub2's os-prober creates a BIOS dual boot, boot stanza, not an efi one.

Boot-Repair was just modified to create chainload entries or you can manually add the correct one to 40_custom.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,[COLOR=Red]gpt2[/COLOR])'
  search --fs-uuid --no-floppy --set=root [COLOR=Red]4f84-ee2e[/COLOR]
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
[COLOR=Red]Red[/COLOR] must be your settings:

THis works for everyone
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

---

### Post by erupter on 2012-08-09
> **2F4U said:**
> Did you already look into the log files? They may give a hint on what Ubuntu is waiting during shutdown. I would suspect that it is waiting on a hardware component to be shut off and the log files should indicate which component it is.

You are right, I should have checked before asking...
Which of the tons of logs of linux?

> **oldfred said:**
> Do not know about video.

If dual booting grub2's os-prober creates a BIOS dual boot, boot stanza, not an efi one.


No dual boots, I've installed it on a separate drive, and I use the motherboard boot menu to switch which drive is booted.
The problems with the pendrive boot also precede the installation.

---

