---
title: "I broke grub"
date: 2011-12-28
forum: General Help
---

### Post by dh04000 on 2011-12-28
I installed MineOS Crux on my laptop's hard drive, instead of the usb hard drive I was trying to install to. Luckily, it installed onto of an ACER recovery drive and not my Win7 or Kubuntu installation. I deleted the MineOS Crux drive and swap(18.1 unallocated), and ran install grub and update-grub using a usb drive with Ubuntu 11.10, but it still tries to boot MineoS Crux using Lilo.  

Using my usb-drive with Ubuntu 11.10 on it and a working wifi connection, how can i fix this?

EDIT: I added boot to Kubuntu's EXT4 drive, that wasn't on it at first. I though that would help, but I've got no idea if it will.

Thanks.

I did this.... [[IMG]http://img11.imageshack.us/img11/7880/screenshotat20111229034.th.png[/IMG]](http://imageshack.us/photo/my-images/11/screenshotat20111229034.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by tomski on 2011-12-29
considering you still see lilo you have 2 options:

1) re-configure lilo & stick with it
2) re-install grub

what you have done previously is just attempt to update grub but alas lilo is where grub should be so look through the ubuntu documentation for instructions on a re-install of grub using the live cd & don't forget to chroot into you kubuntu install otherwise you will be attempting to re-install grub in a live cd environment :)

---

### Post by tomski on 2011-12-29
here are some links to the relevant pages

re-install Grub2 from live cd (chroot) [forum post]
[http://ubuntuforums.org/showpost.php?p=11061340&postcount=5](http://ubuntuforums.org/showpost.php?p=11061340&postcount=5)

recover after windows install [ubuntu documentation]
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Grub2 (good for customization & other commands used by Grub2) [Ubuntu Documentation]
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by dh04000 on 2011-12-29
Thanks, that did the ticket. Now I can log into Ubuntu. One new  problem now though, grub did not recognize Win7, even after a fresh update-grub.

Any ideas?

---

### Post by tomski on 2011-12-29
hmm no i'm afraid not as i too dual boot with xubuntu & win 7 

however i shall poke around google & it would be cool if you could post a linkback to what solves the issue & i will too if i find anything relevant

---

### Post by tomski on 2011-12-29
just a thought 
is windows install on a primary partition or logical partition?

i ask as i am seeing issues like this where win7 is installed on a logical partition

---

### Post by dh04000 on 2011-12-29
I have tried to make a custom grub2 entry. By editing this file: etc/grub.d/40_custom     with this entry.

menuentry "Windows 7 (loader) (on /dev/sda3)" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
chainloader +1
}

Grub doesn't put any entry at all in the menu after a sudo update-grub though.....

---

### Post by dh04000 on 2011-12-29
> **tomski said:**
> just a thought 
is windows install on a primary partition or logical partition?

i ask as i am seeing issues like this where win7 is installed on a logical partition

I think that Win7 is a normal partition while Ubuntu is on a logical.

---

### Post by dh04000 on 2011-12-29
I just tried grub-emu and got this: 

grub-emu: error: cannot guess the root device. Specify the option `--root-device'.


EDIT: This doesn't help. It brings me to the grub menu with grub-emu --r

The grub menu only has >grub

No options at all.

EDIT2: I just tired the application boot-repair and that didn't help either....

---

### Post by dh04000 on 2011-12-29
I really need to get into Win7.

Here's a pastebin of my boot-repair result.

[http://paste.ubuntu.com/787142/](http://paste.ubuntu.com/787142/)

I'm getting desperate.

---

### Post by dh04000 on 2011-12-30
Ended up formatting my hardrive and install Win7 from my recovery discs.

It was a crappy solution, but it got me running again.

---

