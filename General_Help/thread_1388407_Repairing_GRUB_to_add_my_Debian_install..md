---
title: "Repairing GRUB to add my Debian install."
date: 2010-01-23
forum: General Help
---

### Post by kajman on 2010-01-23
Hi!

I have a problem with grub. I've tried to install Debian 5.0.3 on a separate system partition and it all went well except the grub setting (couldn't install the grub/boot(?) on my /dev/sda partition as I have in Kubuntu, but only to /dev/sdaX or /dev/sdbX, where X is a number, so I've chosen one of them). After that install I had a messy grub, with some entries for a Debian system (but it looked as if there where Kubuntu entries, with a name changed to Debian, because I had 3 of them, as many as linux kernels in Kubuntu, but not sure here). None of those Debian entries worked, just showed some boot error, I think numbered 22. So I've forgot about Debian and reinstalled Kubuntu 9.10.

Now I have two questions:
1) How to repair grub in such a situation to get back the access to other systems? I have made 3 separate partitions for installing different linux systems, to test them, but I'd like to be always sure that, if something goes wrong I can get back to my Kubuntu which I use every day. Is it possible? 
2) Update-grub command gives this output:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
Found Debian GNU/Linux (5.0.3) on /dev/sda5
done

```
Why is that I don't see the Debian entry after a reboot? (It's my old install from the story above, I didn't format the mentioned /sda5 partition after the failure). What can I do to finally enter this never-used Debian system?

---

### Post by quixote on 2010-01-25
I got reasonably good at grub-legacy, and then they went and changed everything to grub2 ....  So all I can really do is point you to the posts that I'm using to learn the new grub, but maybe that'll help.

[Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275").  Most relevant for you, perhaps, are #6. Adding Entries to Grub 2, #13. Reinstalling GRUB 2 from the LiveCD, and #16. Restoring GRUB2 / XP / Vista / Win 7 Bootloaders.  There's also a lot of useful grub2 links at the end.

When you put grub on /dev/sdaX, it's on a partition rather than in the Master Boot Record for that drive.  That's not a problem, but something in the MBR does need to point to grub or else it won't be used.  #16 above addresses that, although it's not a method I've used myself.

As for accessing the Debian installs, that's a matter of getting the right menuentry lines into the 40_custom file in /etc/grub.d/, which is discussed in #6.  update-grub is supposed to just find new bootable partitions, but if it doesn't, then that's the manual method.  The only problem is, they don't have very many examples.  Maybe search on something like "ubuntu grub2 menuentry Debian"?  

(Don't forget that grub2 has the weirdest numbering scheme: start from 0 for drives, start from 1 for partitions. I think they did it on purpose as an intelligence test or something :rolleyes:.)

---

### Post by oldfred on 2010-01-25
Keep a copy of these instructions and your liveCD handy and you can always reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

When you install other systems, just do not overwrite the MBR and you never will have a problem. An update grub in Karmic should find your other installls and let you boot them. Sometimes manual entries have to be made into 40_custom for some installs.

Error 22 for old grub was no such partition. Usually something was mis-identified.
[http://members.iinet.net.au/~herman546/p15.html#22]("http://members.iinet.net.au/%7Eherman546/p15.html#22")

If your other install has old grub you can install it to the PBR partition boot record instead of the MBR and chainboot from grub2 to the install's partition with an entry like this in 40_custom:

# Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#chainloader_boot_entry]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Configuration%20File%20Commands.html#chainloader_boot_entry")

This just jumps to the install of grub in the partition in a manner similar to the way it jumps to the windows boot in a partition boot record.

---

### Post by Leppie on 2010-01-25
what you could try is boot manually into Debian, install grub2 from there. we know that Ubuntu works properly with grub2, but i believe that in debian it's still in alpha phase.

---

### Post by kajman on 2010-01-25
Thank you all for replies!

As soon as I have some spare time (the term is coming to an end, so I have a lot of to learn now :)) I'll check some of the solutions provided, and read this information you gave me.

Once again, thank you all for help.

kajman

---

