---
title: "cannot mount selected partition"
date: 2009-11-02
forum: General Help
---

### Post by bruceshwen on 2009-11-02
I installed Ubuntu 9.0.4 on my laptop few week ago and was happy about it. I use dual-boot configuratioin between Ubuntu and Windows XP.
 
Last weekend I upgraded to Ubuntu 9.1.0 (32-bit) through the upgrade manager. The upgrade went smoothly. But when I restarted my laptop at the end of the upgrade process, it failed to restart and it showed the following message:
 
Error 11: cannot mount selected partition. 
 
I tried few times. Now all the boot options for Ubuntu show the same error. I could only boot to Windows XP.
 
Do I need to modify Grub or other setup manually to get the upgrade to complete?
 
Thanks,

---

### Post by Giblet5 on 2009-11-02
It sounds like the upgrade failed...

Do you have a backup?

You can try reinstalling the boot-loader:

Boot from the live CD. Bring up a terminal window.

Run ```
sudo fdisk -l
```

Which extN device is your / filesystem? Let's assume it's /dev/sda2:

```
sudo mount /dev/sda2 /mnt -text
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo chroot /mnt bash ## DANGEROUS! ENTER COMMANDS EXACTLY!
update-grub
grub-install /dev/sda
exit
sudo reboot
```

Now the grub menu should work correctly.

---

### Post by bruceshwen on 2009-11-05
I tried those commands, it did not help.
 
When I started the Ubuntu 9.1 in recovery mode, it did come up. But I could not use the mouse. I think some of my hardwares are not compatible or recognized in the new release.
 
I remove 9.1 and rolled bak to 9.0.4.

---

