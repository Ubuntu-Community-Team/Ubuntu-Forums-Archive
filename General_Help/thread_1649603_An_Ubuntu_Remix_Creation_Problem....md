---
title: "An Ubuntu Remix Creation Problem..."
date: 2010-12-20
forum: General Help
---

### Post by vpapakir on 2010-12-20
Hello all!

I am trying to create an Ubuntu remix live/install cd. I followed the instructions from the "LiveCDCustomizationFromScratch" community document, taken from here:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I followed the instructions, added some packages and created a bootable iso image, as the document describes. I ended up with a approx. 500MB iso image that worked like a charm!

Then, i started over but in the middle of the process, i downloaded the latest stable linux kernel, from kernel.org, i built it into my chroot (thankfully, no problems appeared), added some extra stuff and re-packaged it. I ended up with a 1,1 GB iso image. When i try to boot that image, shortly after vmlinuz and initrd are loaded, i get the error message:

```
"(initramfs) mount mounting /dev/loop0 on filesystem.squashfs failed: Input/Output error
Cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs on // filesystem.squashfs"
```

and nothing else happens. I googled it a little bit, but i haven't found any satisfying solutions. Could that be because of the size of the iso (maybe mkisofs needs some other arguments) or is it something else?

Thank you!

---

### Post by vpapakir on 2010-12-21
Hmm, i guess that still remains a little tricky for all users out there!!!! Nevertheless i have found a workaround by repeating the process and invoking the command "sudo update-grub2" just before i exit chroot. 

Unfortunately now i have another problem: kernel boots but leads me instantly to something that looks like kernel debugging. I wouldn't have had any problem with that, but it takes too long!!!! Any ideas now?

Thank you!

---

