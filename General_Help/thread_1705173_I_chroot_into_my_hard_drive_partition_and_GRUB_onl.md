---
title: "I chroot into my hard drive partition and GRUB only sees Windows 7!"
date: 2011-03-11
forum: General Help
---

### Post by s3a on 2011-03-11
I chrooted into my partition via a live DVD and did grub-install /dev/sdb (the hard drive/partition I want grub to see) and grub-install /dev/sda (the Windows 7 hard drive). I even tried to make the BIOS look at my Windows drive second but GRUB still only detects Windows! Just to be clear, it's not that Windows just starts. GRUB actually behaves normally up until the choice of what to boot.

I had also done update-grub when chrooted! What else can I try?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by wilee-nilee on 2011-03-11
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between. This will let us know what is where, and make things a bit easier.

---

### Post by s3a on 2011-03-11
Your script doesn't work since I'm trying to recover a Debian system with a 10.04 LTS Live DVD. I guess that's my fault though for not saying.

---

### Post by wilee-nilee on 2011-03-11
So did you chroot the grub into the debian install in sdb and put the grub loader in sda?

Do you know what grub Debian is using grub-legacy or grub2? I ask as I believe it is grub-legacy but 10.04 is grub2, if you used that disc to reinstall grub.

I would think the script should work it generates a text file to post. Debian is not much different the Ubuntu, the same basic framework is there. 

Were you expecting the script to fix something?

---

### Post by s3a on 2011-03-11
I installed grub in both sda and sdb. It's using grub2. As proof, I converted ext3 to ext4 (and use ext4 specific features). A quick look at the code of the script seems to be that it looks for Ubuntu-specific stuff. I know Debian and Ubuntu are similar :). I was only expecting to post more information to get more help from the script.

---

### Post by wilee-nilee on 2011-03-11
If Debian can boot supergrub will get you in, from there you can do the voodoo I think you know what to do.;)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Get the one in the middle, I use this as a cheat all the time as I install lots of OS's and like one specific distro to have grub control, a stable one lol.

---

### Post by s3a on 2011-03-11
Thanks for the suggestion but I don't see how "improperly" booting into Debian will be any different than chrooting into it to fix the problem. I can run the same commands in both cases. Any reason to suggest I'm wrong? (Even though, this probably still doesn't solve the problem, that super grub disk seems nice).

---

### Post by wilee-nilee on 2011-03-11
> **s3a said:**
> Thanks for the suggestion but I don't see how "improperly" booting into Debian will be any different than chrooting into it to fix the problem. I can run the same commands in both cases. Any reason to suggest I'm wrong? (Even though, this probably still doesn't solve the problem, that super grub disk seems nice).

It sounds like you have done everything right, the sda mbr wasn't needed but wouldn't normally block the setup. For me once in a while the regular stuff that should work doesn't. I had Maverick not let me reload grub to the mbr and boot at one point, the script said it was fine, I know this stuff I was flummoxed. I remembered the supergrub disc and have used it from a multiloaded thumb every time now I just boot back into Mav to set it as the booting OS.

Part of the problem may be that the grub2 on the Ubuntu dvd may be different then the one from Debian, the distro's will tweak them for the OS. I had never thought about this until I saw a post by a forum member who really knows this stuff commenting about this. I'm assuming you have used the Ubuntu dvd to reload the 2 mbr's and the Debian partition.

The supergrub disc isn't really a improper boot in, it is just able to find the boot from the distro to get in, once in you can remove the cd or thumb what ever you used.

---

### Post by s3a on 2011-03-11
Ok and using the super grub 2 disc is likely to solve my problem regardless of which Linux distro I use?

---

### Post by wilee-nilee on 2011-03-11
> **s3a said:**
> Ok and using the super grub 2 disc is likely to solve my problem regardless of which Linux distro I use?

I think so it is just set to look for the boot stuff in the distro. I have never used it with Debian, but it should work if it is in working order. I see hits on Google with people using it.

---

### Post by s3a on 2011-03-11
I downloaded this: [http://download.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso](http://download.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso)

and burnt it to a CD and when I boot from it, it says:

```
error: unknown filesystem
entering rescue mode...
grub rescue>
```

What do I type now? Is this normal?

---

### Post by wilee-nilee on 2011-03-11
> **s3a said:**
> I downloaded this: [http://download.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso](http://download.berlios.de/supergrub/super_grub_disk_hybrid-1.98s1.iso)

and burnt it to a CD and when I boot from it, it says:

```
error: unknown filesystem
entering rescue mode...
grub rescue>
```

What do I type now? Is this normal?

Shouldn't be, sometime though you need to use the per-session key prompt to boot a cd or thumb, the bios with them first sometimes doesn't work. My key prompt is f12, yours may be a different one. This prompt gives you a out of the bios boot from menu.

I'm assuming you have also burned the ISO as an image.

So additionally it sounds like you got to the disc boot but when you choose the kernel hit you get this error is this correct? The disc has several methods so if you get it to boot you have to try the options. It may be though that the error is due to a corruption.

---

### Post by s3a on 2011-03-11
Actually, it doesn't ask me anything at all. It just goes there. The k3b program confirmed the burn to be successful. Also, I did burn it as an image. As for f12, I did that too. (I have to since I use a USB DVD drive).

---

### Post by wilee-nilee on 2011-03-11
You should see the gui on this page from choosing the cd.
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

Try a thumb and unetbootin, if you have one.

---

### Post by s3a on 2011-03-12
I don't see that. I tried both flash drive with unetbootin and CD. Neither work. I even tried using the windows bootloader to remove GRUB then re-chroot and do the same and I'm back at GRUB booting only Windows.

---

