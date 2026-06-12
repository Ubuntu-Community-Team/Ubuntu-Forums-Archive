---
title: "Guide me through triplebooting Vista, Lucid and OS X??"
date: 2010-05-16
forum: General Help
---

### Post by sirspazzolot on 2010-05-16
I have Vista and Lucid dualbooting with GRUB. Could somebody guide me through what I should do from here? Or send me a link to an existing guide? Preferably for installing a newer version of OSX. I've been looking around and I can't seem to find much about doing this. Thanks in advance. :)

---

### Post by sirspazzolot on 2010-05-16
Please?

---

### Post by ryan858 on 2010-05-16
All you need to do is add OS X to grub... How to do that though, is beyond me.

Do you know what kind of boot-loader OS X uses? If it's similar to grub, then you may just copy the parameters, but it's probably not remotely similar, although OS X is UNIX-based I believe.

---

### Post by sirspazzolot on 2010-05-16
It is UNIX-based. I don't know how to add it to GRUB either, or really how to install it in the first place. Just find a LiveDVD and run it and install it? Then I really don't know how to get it into grub. I don't know how to do anything with Grub, I don't understand it. I need to choose Vista Recovery Environment to boot Vista and I need to choose Vista to boot the recovery environment. I guess I'll search around. I know people have done it, they just never explain how.

---

### Post by ryan858 on 2010-05-16
Well, I would say Google "adding OS X to Grub2".

In the mean time, if you have the other OS's installed on separate hard drives (not partitions, *whole other drives*), then you can choose which one to boot with during POST by using the boot selection menu. It's F11 on my machine... It should tell you when you first turn the computer on, e.g. "Press F11 for boot choices", etc. It may be F12 or F10 too. Or you can get into the BIOS setup (usually Delete key) and get rid of the OEM Logo. That will usually show some other options if they weren't shown before.

But if you have them all on the same disk, then, well, you're outta luck... Until you get OS X into Grub2

---

### Post by sirspazzolot on 2010-05-16
How convenient. I'm getting an external hard drive tomorrow. I'm sure there's a guide to this out there somewhere. I just have to find it. If I install OSX on the external drive would I still be able to plug it into my computer and use it? Or would I not have access to the insides of the disk because of some wacky Apple thing?

---

### Post by Cathhsmom on 2010-05-16
This link might lead to some help.  I came across this while reading Ubuntu Guide today: [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_multiple_OS_on_a_single_computer]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_multiple_OS_on_a_single_computer")

---

