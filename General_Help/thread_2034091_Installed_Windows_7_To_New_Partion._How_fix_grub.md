---
title: "Installed Windows 7 To New Partion. How fix grub?"
date: 2012-07-27
forum: General Help
---

### Post by SageO on 2012-07-27
Well I was completely on Ubuntu 12.04 for a while.
Just last night I installed Windows 7 64 bit after creating an ntfs partition for it.
Now I can only boot into Windows. I heard that I'd have to fix GRUB to be able to get back into my Ubuntu installation.
How would I go about doing that?
(I've got a live bootable Ubuntu USB with GParted on it)

---

### Post by angry_johnnie on 2012-07-27
all you need to do is re install grub:

[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

link has instructions to install it from live cd.  it's the same thing if you have a live usb.  should work. :P

---

### Post by oldfred on 2012-07-27
The link angry_johnnie posted is the longer method we have to use if the short method does not work. And now you can download into your liveCD or USB a gui app to repair installs. 

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version :
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by angry_johnnie on 2012-07-27
Thanks oldfred.  I had no idea! :)  That boot repair app should come in handy in the future.

---

### Post by SageO on 2012-07-29
> **oldfred said:**
> The link angry_johnnie posted is the longer method we have to use if the short method does not work. And now you can download into your liveCD or USB a gui app to repair installs. 

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version :
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda


# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Thanks, I'm gunna give the first link a try and get back to this thread.

---

### Post by SageO on 2012-07-29
> **SageO said:**
> Thanks, I'm gunna give the first link a try and get back to this thread.

Okay grub seems to be working as I'm posting this via my Ubuntu installation :)

But how do I simplify the grub menu? When it boots I see at least two option for ubuntu, then an option that says "previous versions of linux", then two "memory tests", then finally windows.

---

### Post by raja.genupula on 2012-07-29
you can use grub-customizer . A simple grub editor it is . look at my signature to get it .

---

### Post by SageO on 2012-07-29
> **raja.genupula said:**
> you can use grub-customizer . A simple grub editor it is . look at my signature to get it .

Well, I was able to narrow it down to: Ubuntu generic 2.blablaba etc, Ubuntu generic etc etc blabla recovery mode, and Windows 7.
How would I clean up the display text of each option?
Like make it say: Ubuntu, Ubuntu Recovery, & Windows 7. Clean and simple, not messy.

---

