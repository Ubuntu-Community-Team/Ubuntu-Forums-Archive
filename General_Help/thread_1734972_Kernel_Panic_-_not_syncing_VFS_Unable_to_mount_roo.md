---
title: "Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"
date: 2011-04-20
forum: General Help
---

### Post by dark3lf on 2011-04-20
Hello,

I am currently running the latest version of Ubuntu (10.10 I believe) and recently installed a new, vanilla 2.6.37.1 kernel on my machine. Then, all I did was run update-grub (I'm not sure if this is correct as I am new to GRUB2 :/), rebooted and tried to boot into the new kernel, but I got the above error on boot. Does anyone know why this is happening? Thanks in advance!

---

### Post by drs305 on 2011-04-20
Hi *dark3lf*, welcome to the Ubuntu Forums.

Have you tried booting an older kernel?  If one is not listed in the Grub2 menu but you know you still have an older one of the computer you could highlight the new kernel in the Grub2 menu, press 'e', and then edit the lines to show the older kernel version. Once you have made the changes, press CTRL-x to boot. 

If the above works, we will have to edit the grub menu or you can try reinstalling the newer kernel.

Otherwise, please download the boot info script from the following site and post the RESULTS.txt it generates.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by dark3lf on 2011-04-20
Thanks for the reply. Yes, I am able to boot into a different kernel, so that's not a problem (I am just trying to boot into the new 2.6.37.1 one). The results file is attached.

---

### Post by drs305 on 2011-04-20
Your /boot/grub/grub.cfg menuentries for 2.6.37.1 do not contain an *initrd* line. It's normally the last line before the **}**.

If you look at the last section of the RESULTS.txt it shows what I suppose is an initrd image, but it's named 'initrd.img-vmlinuz-2.6.37.1". There is also a similar "-generic" one.

I suppose you could try to add a last line as the following but I don't know if it would work. I suppose the actual name may not matter as long as it exists:
```
initrd /boot/initrd.img-vmlinuz-2.6.37.1-generic
```
Before I went to a lot of trouble with this I'd just open /boot/grub/grub.cfg and paste it in the appropriate line. Save the file, then reboot WITHOUT running update-grub (which would erase the change). If it works you will have to do some permanent menu work - we can deal with that later.

The other thing you could try would be to regenerate the initrd image with:
```
sudo update-initramfs -k 2.6.37.1
```
I don't know if this will produce a workable image or not. If you try it, in this case you WOULD run update-grub if it makes a proper initrd image file.

---

### Post by dark3lf on 2011-04-20
I tried just adding in the line to my grub.cfg, saving but not running update-grub, and rebooting like you said and I got the following errors:

FATAL: Could not load /lib/modules/2.6.37.1/modules.dep: No such file or directory
ALERT! /dev/sda1 does not exist. Dropping to a shell!

Should I proceed with trying to create a new image like you said?

---

### Post by drs305 on 2011-04-20
> **dark3lf said:**
> Should I proceed with trying to create a new image like you said?

It won't harm anything and it might build the correct initrd image.

I can tell you why Grub2 isn't working but I am not someone who compiles his own kernels. It's probably pretty basic knowledge for those that do, but I don't know if you can build a 37 version's intird with the command while running 35, but you can try it.

If it runs and then you run update-grub, check the menuentry to see if the initrd line has been properly added.

---

### Post by dark3lf on 2011-04-20
So i created the new image successfully and when I ran update-grub, it added the image correctly in the grub.cfg file. However, when I rebooted I got the following errors:

ALERT! /dev/disk/by-uuid/a284401f-a3fc-44ea-b31f-5141f7278168 does not exist.

Any more suggestions?

---

### Post by drs305 on 2011-04-20
The UUID's appear identical in RESULTS.txt as far as I can tell (in blkid, fstab and the menuentries).

Open up your /boot/grub/grub.cfg file.

Take a look at a menuentry that normally boots and compare it to the new kernel's entry. Look specifically at any UUIDs and /dev/sdXY settings. If you find any difference, change the offending menuentry to match the good one.

If nothing else, you can try to remove the entire 'search line'. If the 'linux' line in your test kernel contains a UUID, try changing the entry to root=/dev/sda1 (or whatever the value should be).

---

### Post by dark3lf on 2011-04-20
I looked at the menu entries for both the test kernel and the old kernel and they are both exactly the same, save that the old kernel's version number is proceeded by "generic" where as the test kernel is not (I have no idea why that is).

> 
If nothing else, you can try to remove the entire 'search line'. If the  'linux' line in your test kernel contains a UUID, try changing the entry  to root=/dev/sda1 (or whatever the value should be).


To be honest, I am not even sure I know exactly what partition the test kernel is on, that is when I compiled and installed the new kernel I was never prompted to choose a partition. How do I check where it is?

---

### Post by drs305 on 2011-04-20
I reviewed your old RESULTS.txt and recalled you really only have one system partition (sda1).

I don't know if the kernel you compiled has some special requirements or not. 

I'd remove the UUID and replace it with /dev/sda1. You might even edit your fstab and replace the UUID= with /dev/sda1.

Note there is an option to turn off UUIDs in Grub2 in /etc/default/grub. Just uncomment the "GRUB_DISABLE_LINUX_UUID=true" line and update-grub

One other thing you could check would be at a failed boot at the initramfs prompt, type the following to check what partitions and UUIDs the OS is seeing:
```
ls /dev/sd* /dev/disk/by-uuid
```

You could post a new RESULTS.txt but I'm just about out of ideas since I suspect this is a kernel problem.

---

### Post by deconstrained on 2011-04-20
drs305 has given sound advice. I second the motion to give rebuilding your initrd a shot ;-)

---

### Post by dark3lf on 2011-04-20
> ls /dev/sd* /dev/disk/by-uuid 

When I try both ls /dev/sd* and ls /dev/disk/by-uuid at the initramfs prompt i get "no such file or directory".

Also, I am getting this error:
ALERT! /dev/sda1 does not exist

The new results file is attached...

---

### Post by drs305 on 2011-04-21
> **dark3lf said:**
> When I try both ls /dev/sd* and ls /dev/disk/by-uuid at the initramfs prompt i get "no such file or directory".

Also, I am getting this error:
ALERT! /dev/sda1 does not exist

Is this happening only when you select your new kernel? (i.e. do your older Grub2 menu items still work correctly). If so, I'd probably just purge the newer kernel if rebuilding the initrd.img didn't solve it.

---

### Post by dark3lf on 2011-04-21
> Is this happening only when you select your new kernel? (i.e. do your older Grub2 menu items still work correctly)

That's correct. If I select any other menu item it will just boot right into it without any prompt or anything. After I delete the new kernel what do you suggest I do differently when I reinstall it? I think just trying over again from scratch may fix it, but I'd rather not go through the whole process again unless I'm confident that this time it'll work...

---

### Post by drs305 on 2011-04-21
> **dark3lf said:**
> After I delete the new kernel what do you suggest I do differently when I reinstall it? I think just trying over again from scratch may fix it, but I'd rather not go through the whole process again unless I'm confident that this time it'll work...

No more kernel answers from me, as I'm unqualified to offer much advice on the matter.  ;-)

However, if I were going to try it, here is a link I might follow:
[http://www.khattam.info/howto-install-linux-kernel-2-6-36-or-2-6-37-in-debian-squeeze-testing-or-ubuntu-or-any-debian-based-distribution-without-compiling-2010-11-13.html]("http://www.khattam.info/howto-install-linux-kernel-2-6-36-or-2-6-37-in-debian-squeeze-testing-or-ubuntu-or-any-debian-based-distribution-without-compiling-2010-11-13.html")

Happy Ubuntu-ing !

---

### Post by rputnins on 2011-06-10
Hi!

I found this post because I have the same error, yet the problem seems different.

I have ubuntu 11.04, latest PAE kernel and this is my results file of boot info script.

Now what I see if I compare this file with some other machine of mine (ubuntu 11.04, latest kernel without pae support) - the place (?) of main boot files is not at the beggining of the disk:

```

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 226.185737610 = 242.865086464  boot/grub/core.img                             1
 144.190746307 = 154.823634944  boot/grub/grub.cfg                             1
  49.223834991 = 52.853690368   boot/initrd.img-2.6.38-8-generic-pae           1
 152.782653809 = 164.049125376  boot/vmlinuz-2.6.38-8-generic-pae              1
  49.223834991 = 52.853690368   initrd.img                                     1
 152.782653809 = 164.049125376  vmlinuz                                        1

```

Is this the problem? As I can't find any other differences for those two computers.

And the main question - how to fix it??

Thanks in advance!

---

### Post by drs305 on 2011-06-10
> **rputnins said:**
> Hi!

I found this post because I have the same error, yet the problem seems different.

I have ubuntu 11.04, latest PAE kernel and this is my results file of boot info script.

Now what I see if I compare this file with some other machine of mine (ubuntu 11.04, latest kernel without pae support) - the place (?) of main boot files is not at the beggining of the disk:

Do you have reason to suspect it's a BIOS drive size limitation? 
Have you entered BIOS to check the reported disk size (if it shows 137GB or less that could be the problem)? 
At the grub prompt (press 'c' to get there from the Grub menu), if you run "ls (hd0,1)/boot/grub/core.img" does it find the file?

---

### Post by rputnins on 2011-06-13
Well I can get Grub2 promt and grub finds the file. I checked the disk with fsck and it is ok, no problems, Livecd can browse and write, but I still can't boot system - kernel panic unable to mount root fs on unknown-block(0,0)

---

### Post by psusi on 2011-06-13
You need to build the initramfs to go with the kernel image, using update-initramfs.

---

### Post by rputnins on 2011-06-13
> **psusi said:**
> You need to build the initramfs to go with the kernel image, using update-initramfs.

Thanks for tip! How to do this using LiveCD?

---

### Post by psusi on 2011-06-13
Why don't you just boot the previous working kernel instead of using the livecd?  Then run sudo update-initramfs -c -k kernelversion.

---

### Post by PavelMan on 2011-08-07
I have an exact same problem, with the same error message. It is just previous kernels do not boot either.

I had to boot from the flash (sdb1 in the RESULTS) to collect this info.

Did anybody manage to solve this puzzle? It was a working system before, but stopped working after "some updates". Unfortunately, this happened a few months ago, and nobody remembers which update that was...

ls (hd0,1)/boot/grub/core.img says "core.img" in response, so I assume it is visible.

---

