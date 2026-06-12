---
title: "Boot question - I'm missing something simple!"
date: 2012-09-09
forum: General Help
---

### Post by cjhabs on 2012-09-09
Hi

I have a laptop running 10.04 on the internal drive - sda - that is working great.
I have an external usb - sdb - that boots first if connected. On there I have 3 OS partitions - all primary:
sdb1 = 12.04 - installed from dvd - works great, boots correctly
sdb5 = another 12.04 - installed from dvd - works great, boots correctly
sdb4 = a copy of my live 10.04 os - this is causing me an issue.
I created it by doing a dump of my 10.04 while running off an os on the external drive. Then I restored the dump to sdb4.
I then edited fstab to mount root off sd4 and swap off the external disk (home is still off the internal sda drive).
I then ran update-grub.
When I reboot, I see sdb4 as a boot option - I boot from it - it brings up the os running off sda1 - the internal disk.

What am I missing?

Thanks

Proz

---

### Post by oldfred on 2012-09-09
Where did you run update-grub.

The grub.cfg in sdb4 probably still is the sda1 one, so a update-grub from other installs is reading the grub.cfg? I think a update-grub first looks for grub configurtion files - (grub.cfg, menu.lst and others) files to use and only if not found may look for kernels to use in a menu. You would have to run update-grub  from inside the sdb4 install to update its grub.cfg.

You can post the BootInfo and see the details:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by cjhabs on 2012-09-10
Thanks for the suggestion, I tried the following:
Booted from the external drive (sdc1), I ran:
sudo update-grub sdc4
then
sudo update-grub

They both gave exactly the same message, saying that an OS was found on sda1, sdc4 and sdc5.

Booting from sdc4 still mounts sda1 as the root.

Any other ideas I can try?

Thanks

---

### Post by oldfred on 2012-09-10
You would have to chroot into the install to run the update-grub from it. There is no other way to update it.

While the rules say never to edit grub.cfg, rules can be broken. And your case may be easier to edit the first entry to have the correct UUID and partition. Not sure if update grub from another install will then work correctly for that entry or not. Or you install grub for sdb4 or is it now sdc4 into the MBR to boot and run sudo update-grub. Then you can reinstall the grub to the MBR that you want.

mount /dev/sdb4 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg
Other suggestions that I have seen, these are from inside the install so /mnt is missing:
grub.cfg is read only and should not normally be edited:
sudo chattr -i /boot/grub/grub.cfg
gksu gedit +28 /boot/grub/grub.cfg
sudo nano /boot/grub/grub.cfg



You can use Boot-Repair or command line to install grub2's boot loader to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb or any other install of Ubuntu, Ubuntu install on sdb4 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb4 if not correct:
sudo fdisk -l
#confirm that linux is sdb4
sudo mount /dev/sdb4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Then from that install you should be able to boot into any other install.

If you want a differnt install in the MBR, so it is first on menu. Boot into that install and run this:
#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by cjhabs on 2012-09-10
I took the easy way out!
I edited /boot/grub/grub.cfg on the sdb4 root partition (mounted while running an os off another partition) and changed the UUID to sdb4 - I took the opportunity to edit out the old kernel menu items.
While booted from the external drive (sdb1), I ran:
sudo update-grub
I rebooted - selected sdb4 from the boot menu and voila - it booted off the appropriate partition.

Thank you - the system is working great.

Next I need to bite the bullet and upgrade to 12.04 - not tonight though!

---

### Post by cjhabs on 2012-09-11
Thanks for the quick help - it was much appreciated.

---

### Post by oldfred on 2012-09-11
You are wlecome. Glad it worked. :)

---

