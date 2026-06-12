---
title: "[ubuntu startup disk] Hangs at startup on Ubuntu image"
date: 2011-08-21
forum: General Help
---

### Post by Matifou on 2011-08-21
Hi

I recently installed the Ubuntu startup dsik on an external HDD, which I use as a portable version of Ubuntu everywhere I go :-)

It now hangs at startup.... i.e., it comes to the "ubuntu" page, with the red& white rounds below, and does not go further... after 1 hour, the red point is still running... 

I tried to see what was hapening, reading that disk from another computer, inspeted the /var/log syslog and boot, but I see nothing comes written there: it seems it has not reached that level... Any idea of a strategy I should follow, to try to figure out where the problem is?

Thanks!!

Matt

---

### Post by sanderd17 on 2011-08-21
See my signature about setting boot options, but remove the boot options "quiet splash". That way you will get an output.

---

### Post by Matifou on 2011-08-21
Hi

Thanks a lot for your quick reply! I am not sure exactly what you adviced? I did:
boot, press any key -> F6 -> nomodeset->esc and boot. 

But I had the same problem unfortunately! Should I try entering the grub as you said also to set just nomodeset? I was also not able to enter the grub... pushing space brings me to the same install ubuntu/... menu. 

Do you think I should check how grub is configured on the usb flash drive? I did not find a /etc/default/grub file...

Also, I should mention that it used to work before, something happened, I don't know what...

Thanks!!

---

### Post by sanderd17 on 2011-08-21
You should edit the boot options in GRUB, not for the live CD.

The link in my sig just says where you find the boot options (in grub, in the live cd, or permanently), and you need to delete the option "quiet splash" in grub.

You don't need to add boot options like nomodeset.

This will give you some text output, so you will see where it hangs. This won't fix anything.

---

### Post by Matifou on 2011-08-21
Ok, I got it!!!

Now I can see where it hangs:

> EXT2-fs: warning, mounting unchecked fs, runining e2fsck is recommended
can't open /dev/sr0: No medium found
Warning: Unable to find the persistent home medium
can't open /dev/sr0: No medium found
Warning: impossible to include the casper-sn snapshot

Begin:[]
Begin: Adding live session user

This seems to be a known problem! The post on the net were unfortunately quite obscure for me.... Any help would be very acknowledged! How can I make him recognise the right disk where home is?

I should add I had had problems with the ext2 file, so might be the problem! I had many messages like this on /var/log/syslog:
> Aug 17 18:56:41 ubuntu kernel: [ 1744.117197] EXT2-fs (sdb3): error: ext2_lookup: deleted inode referenced: 107612

My USB drive is organised like this:
-boot systems on first partition (fat32)
-casper-rw on a second, containing home (ext2)

Thanks!!

---

### Post by sanderd17 on 2011-08-21
/dev/sr0 is some drive (a floppy or something) that he doesn't seem to find.

Can you try this? [http://ubuntuforums.org/showthread.php?t=1345125&page=2](http://ubuntuforums.org/showthread.php?t=1345125&page=2)

---

### Post by Matifou on 2011-08-21
Nice, seems you have found the right post! I tried but however my grub entry is slightly different... I have:
> noprompt cdrom-detect/try-usy=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper init=/casper/initrd.lz quiet splash--

I have tried:
> noprompt cdrom-detect/try-usy=true persistent boot=casper live-media-path=/casper/ init=/casper/initrd.lz ignore_uuid--

But I still have the same problem, that it tries to open this /dev/sr0... Are there some options I shoul dchange here?


I see it runs /scripts/casper-premount first... should I try to change this?

Thanks!!

---

### Post by sanderd17 on 2011-08-21
can you try the full example like they give it?

I don't know, just a bit of trial and error.

---

### Post by Matifou on 2011-08-23
Well I've tried many combinations, but was still not working...

I posted there:
[http://ubuntuforums.org/showthread.php?p=11173632#post11173632](http://ubuntuforums.org/showthread.php?p=11173632#post11173632)

and will see if anyone answers...

Thanks in any case for your precious help!!

Matthieu

---

