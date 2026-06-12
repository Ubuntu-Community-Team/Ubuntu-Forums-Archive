---
title: "INITRD + GRUB // Multiboot"
date: 2011-12-06
forum: General Help
---

### Post by mattzab on 2011-12-06
Hello,
 
I'm not exactly sure if this is possible, and the googling ive done hasn't turned up with anything specific to my question here.
 
I run primarily Ubuntu 11.04, but I have Windows 7 and OS X installed on the same drive on different partitions.
Part 1:
I installed OS X using a tonymacx86 tutorial which has a CD called iBoot. To make things short and simple, the bootloader for OS X simply doesn't work. For some reason from what I can tell, it just doesnt stick when installed. Everything in OS X runs fine, except for the fact that I can't boot into it directly. If I want to boot to OS X, I have to have the iBoot CD inserted and then select OS X from there. GRUB is able to find OS X, but can't boot into it.
Part 2:
I installed windows 7 using HP recovery discs that came with the laptop. Since they aren't true windows install discs, they dont allow for partitioning. They just assume you want to wipe the whole drive and start new with your fancy HP.
So I installed windows 7 to a different, blank, hard drive and then used clonezilla to copy it to the one I currently use in my laptop. GRUB can detect Windows 7 (but lables it as win7 recovery). When I select Windows 7, it fails to boot. I'm missing some files that windows needs to boot up. When I looked at the other drive, I noticed a 200mb partition of space that had windows startup files on it.
 
Question time:
Is there a way I can create my own INITRD.img and just point GRUB to the root partition, then have it load an INITRD.img into memory to continue the boot process? I can only boot Ubuntu, but I'd like to have a triple boot going here. I was considering pulling the files off the iBoot CD and repackaging them as an INITRD.img with a few mods to run off the disk drive instead of a CD. I want to do the same, just use clonezilla or something else like that to extract the needed boot files for windows off that little partition and make an INITRD.img that will load things up.
 
Is this possible? Where should I start? How can I pull this off?
 
Thank you very much.

---

### Post by mattzab on 2011-12-15
UPDATE

Ok, so I placed Preboot.dmg from inside iBoot.iso into a folder called grub on the root of my OSX partition and attempted to boot it using GRUB2.

Here's the code I used:

```
menuentry "Mac OS X INITRD TEST" --class osx --class darwin --class os {
	insmod part_gpt
	insmod hfsplus
	set root='(/dev/sda,gpt2)'
	initrd /grub/Preboot.dmg
}
```

And when I select that option in grub here's what I get:

```
error: no such disk.
error: you need to load the kernel first.

Press any key to continue...
```

I'm confident that I'm pointing grub to the right partition, that's easy to sort out.
However, I don't have grub calling the kernel. I guess.
Any modifications ya'll would suggest?
I don't know how to get grub to load the kernel. There's a file called mach_kernel and I'd assume that's what's needed, but even if I add the line **xnu_kernel /mach_kernel** above the part where it loads preboot.dmg I still get the same errors.


I'm going to keep trying different things. More updates soon to come. Please help me out if you can.

---

