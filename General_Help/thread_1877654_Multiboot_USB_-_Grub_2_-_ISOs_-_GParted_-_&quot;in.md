---
title: "Multiboot USB - Grub 2 - ISOs - GParted - &quot;initrd1&quot; ????"
date: 2011-11-08
forum: General Help
---

### Post by Roasted on 2011-11-08
I'm setting up an 8gb flash drive to contain an array of ISOs which allows me to chain load. I found some directions on pendrivelinux and began to run with it accordingly. 

I got everything running with the current grub config:

```
grub
# This grub.cfg file was created by Lance http://www.pendrivelinux.com
# Suggested Entries and the suggestor, if available, will also be noted.

set timeout=10
set default=0

menuentry "Ubuntu 11.10 32 Bit" {
 loopback loop /home/isos/ubuntu32.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/isos/ubuntu32.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 11.10 64 Bit" {
 loopback loop /home/isos/ubuntu64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/isos/ubuntu64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "GParted Live" {
      set isofile="/home/isos/gparted.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd.img
}

menuentry "Clonezilla Live" {
set isofile="/home/isos/clonezilla.iso"
loopback loop $isofile 
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

menuentry "DBAN" {
 loopback loop /home/isos/dban.iso
 linux (loop)/DBAN.BZI nuke="dwipe" iso-scan/filename=/dban.iso silent --
} 

```

However, I got tripped up on the GParted entry. After Googling "gparted grub2 iso boot" I found this link here:

[http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)

Which has this entry for booting with Grub 2:

```
menuentry "Gparted live" {
      set isofile="/home/isos/gparted-live-0.5.2-9.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz1 boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd1.img
    }
```

Once I booted to GParted, I received an error immediately saying I need to load the kernel first. I began to look at the entry and compare it to the others. I noticed the GParted entry listed on the site had entries for "initrd1" and "vmlinuz1", yet the others did not. On a hunch, I removed "1" from both, and now GParted boots up just fine.

My concern is basically, what is the scoop here? Is this "safe"? I just don't want GParted to completely crap itself when I need it the most because I switched up what kernel it was using or whatever. If somebody can fill in the gaps, that would be great.




[COLOR="Red"]**EDIT - The below section is solved via this link:**[/COLOR] (Still very curious about what's posted above, though)

[http://forums.linuxmint.com/viewtopic.php?f=46&t=46784](http://forums.linuxmint.com/viewtopic.php?f=46&t=46784)

Secondly, I have another question. Both GParted and Clonezilla get a minor error when booting... saying something to the tone of:

vga=788 is deprecated. Use set gfxpayload=800x600x16, 800x600 before linux command instead.

Am I do use 800x600? The x16 throws me off a bit. It passes this error and seems to load fine after, but I'd rather ask and make sure while I'm already making a thread.

Thanks guys!

EDIT - Lastly, is it possible to add Ultimate Boot CD to this menu? I'm not sure what the Grub 2 "menuentry" should be for UBCD... I can't find it anywhere...

---

### Post by bryanl on 2011-11-08
hey, thanks!

I put together a multiboot USB stick but hadn't got around to getting clonezilla and a few other iso images configured. Your code will help me on the way to using it for something other than just choosing distributions. Going through this helps me understand the process and, if anybody sees where I am off base and explains why, I can learn something, too.

As far as 'is it safe' consider what is happening here. To me, it is an amazing feat of software engineering way down in the bowels of the backstage. It is something to study to learn about the boot process and file system handling in systems.

What GRUB does first is to mount the iso as if it were a hard drive or similar device much like the BIOS mounted its boot partition to launch GRUB.

It then transfers execution to the operating system on that mounted file system. That means the GRUB has to be able to find a file on the iso file system and that that file needs to be able to use the file system to make the system go.

Note that these custom CD images for gparted, clonezilla, or whatever need an operating system underneath the featured app. They depend upon that OS for file support, video, keyboard, and so on.

For linux, initrd is the initial, memory based, OS that sets everything up and loads the drivers and whatnot so that vmlinuz, the kernel that actually runs the applications, has what it needs to do its thing.

So what the GRUB items are doing is telling GRUB first to set up the ISO as a file system and then providing the path to the linux kernel boot files along with a set of parameters to pass along to the kernel. The 'DBAN' entry is one for contrast and comparison as its OS is provided in a way different from the usual linux boot. 

So finding the proper names for the initrd and kernel image files is necessary for GRUB to boot them. After they get up and running, you have the linux environment needed for gparted or whatever to run and **it should be as 'safe' in that environment as if you were booting directly from a CD**.

Now what I need to figure out is whether or not (and how) to boot other systems. How do they see the loop system that GRUB gives them? Do they need their own drivers for it or, perhaps, use it via the BIOS mechanisms?

Of course, if you want to use gparted to work of the USB stick that has your ISO images on it, you'd want to run the program and its environment off another device. That's what's nice about the multi-boot USB stick as it allows messing with a systems permanently installed drive without having interference between the software being used and the storage medium being manipulated.

re "*vga=788 is deprecated. Use set gfxpayload=800x600x16, 800x600 before linux command instead. ... Am I do use 800x600? The x16 throws me off a bit.*" -- look for the current list of kernal supported video modes (these are hex values and the tables are around in various places). the '16' is probably the color bit depth. Since these utility CD images need to run on many machines, they often set the video to some common denominator.

---

### Post by Roasted on 2011-11-08
> **bryanl said:**
> 

So finding the proper names for the initrd and kernel image files is necessary for GRUB to boot them. After they get up and running, you have the linux environment needed for gparted or whatever to run and **it should be as 'safe' in that environment as if you were booting directly from a CD**.


Thanks for the detailed response! Just to recap, are you basically suggesting that me changing the entries that were on GParted's site from "initrd1" to "initrd" (along with vmlinuz1 to vmlinuz) is safe to do so? 

What would the explanation be here? Would it be a typo or something? I asked in the Linux IRC chat and nobody knew of initrd or vmlinuz ever existing with a number behind it. :confused::confused:

---

### Post by oldfred on 2011-11-08
I have two gparted boot stanzas & one works & the other does not. But the difference are just different options as near as I can tell.

If a ISO is bootable, sometimes new versions move thing or rename them. I have had to browse the ISO to find file names and perhaps the boot to see what options the ISO uses when booted itself.

Grub2 does not use vga= anymore. But some older kernels may. 
vga=xxx is a deprecated boot option
Use this with your monitor size in /etc/default/grub or if manually creating a grub.cfg in grub.cfg:
GRUB_GFXMODE=1024x768

VGA conversions:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)
[http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

I have some newer ISOs that I just cannot boot as they changed something. So the ISO must be bootable, and not all are.

---

### Post by Roasted on 2011-11-08
Does anybody know how I can get Bit Defender Rescue CD's ISO loaded on here and have that as a boot option?

I saw that Bit Defender was Knoppix based, so I put in (what I thought to be) a Knoppix entry I found online and just edited the path to the iso to match where it really was. To say the least, it didn't work.

Does anybody know how I can get it to work? It'd be SUPER helpful to have on one consolidated drive...

---

