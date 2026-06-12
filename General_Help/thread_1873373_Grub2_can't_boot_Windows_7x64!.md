---
title: "Grub2 can't boot Windows 7x64?!?"
date: 2011-11-01
forum: General Help
---

### Post by markjs on 2011-11-01
So I have three OSs on three separate physical drives.  Both Ubuntu and OS X boot just fine, but Windows 7(x64) just boots to a black screen with a flashing white cursor.

I purposely have it set up with Grub2 installed on the Ubuntu drive so that if you set the BIOS to boot off of either of the other two drives it will boot as if OS X or Win7 are the only OS on the machine (no changes to either drive with the only bootloader being Grub2).  I've tried "sudo update-grub" and I can't see anything wrong in the grub.cfg, so maybe one of you will?

> **"/boot/grub/grub.cfg"]### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ] said:**
> ; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 9a37d646-b3bf-43fe-898d-ecc09355c21f
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=9a37d646-b3bf-43fe-898d-ecc09355c21f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 9a37d646-b3bf-43fe-898d-ecc09355c21f
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=9a37d646-b3bf-43fe-898d-ecc09355c21f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 9a37d646-b3bf-43fe-898d-ecc09355c21f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd2,gpt1)'
	search --no-floppy --fs-uuid --set=root 9a37d646-b3bf-43fe-898d-ecc09355c21f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 96161BAD161B8D7D
	chainloader +1
}
menuentry "Mac OS X (32-bit) (on /dev/sdb1)" --class osx --class darwin --class os {
	insmod part_msdos
	insmod hfsplus
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bc5a9b846e12539f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid bc5a9b846e12539f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sdb1)" --class osx --class darwin --class os {
	insmod part_msdos
	insmod hfsplus
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root bc5a9b846e12539f
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid bc5a9b846e12539f uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

Thanks in advance!

---

### Post by mastapat11 on 2011-11-01
Which hd is win on? in other words, 1st, 2nd, or 3rd?
windows is picky, it likes/has to be on (hd0,0) or it won't boot.

Also, about ur BIOS settings, does that mean if ur turn the Ubuntu & mac drives off then win boots ok?

---

### Post by Mark Phelps on 2011-11-01
When you boot Windows it will think it's on the first drive.

Does Win7 boot when only that drive is connected? If not, it's not a GRUB problem, it's a Windows problem.

If it does, then open a terminal and run "sudo update-grub".  That will regenerate the GRUB config file.  After that, it should boot OK.

---

### Post by markjs on 2011-11-01
> **Mark Phelps said:**
> When you boot Windows it will think it's on the first drive.

Does Win7 boot when only that drive is connected? If not, it's not a GRUB problem, it's a Windows problem.

If it does, then open a terminal and run "sudo update-grub".  That will regenerate the GRUB config file.  After that, it should boot OK.

That's just it, I've done that yet it didn't work.  Like I thought I'd explained before, I purposely kept Grub2 off the other two drives, and as long as BIOS has either them first either of the other two OSs (both Windows and OS X), boot as if they were the only one on the machine.  The Ubuntu drive (the one with grub), when set to be first will boot itself or OS X, but not Windows.  So it has to be a Grub problem but I can't see the flaw in the grub.cfg file.

---

### Post by Mark Phelps on 2011-11-01
Unless I missed it, you didn't answer the question about the Win7 drive booting on its own.

All that GRUB does is hand over control to the windows boot loader, based on the partition identified in the GRUB config file.  If Windows doesn not then boot, it's a Windows boot loader problem, not GRUB.

Also, sometimes, GRUB puts two Windows entries into the config file and mislabels them.  If you have two, try both.

---

### Post by markjs on 2011-11-01
> **Mark Phelps said:**
> Unless I missed it, you didn't answer the question about the Win7 drive booting on its own.

All that GRUB does is hand over control to the windows boot loader, based on the partition identified in the GRUB config file.  If Windows doesn not then boot, it's a Windows boot loader problem, not GRUB.

Also, sometimes, GRUB puts two Windows entries into the config file and mislabels them.  If you have two, try both.

Yeah everyone missed it twice now.  For the (hopefully) LAST time, if you set the Windows drive to be first in BIOS it boots just fine (into Windows), but if you set the Ubuntu drive which is the one with Grub2 installed on it first (in BIOS) then try to boot from the Windows menu entry (in Grub2 booted of the Ubuntu drive, the one with Grub and ONLY Ubuntu on it) it just goes to a black screen with a flashing cursor.

Sorry for my frustration, but I've said it three different ways now, and I'm not sure if I can explain it any clearer than I have.

Let me explain further.  I want the Windows, and the Mac drives to boot by themselves into their respective OSs with no bootloader on them, so that if you physically removed the rest of the drives it would be straight to the OS.  I want Grub on the Ubuntu physical drive.

Now I know, if I put Grub2 on the windows drive I probably would have access to all three OS's but if I took out the other drives, I'd have to go through the grub menu which I don't want on that drive.  I know this because someone else had the exact problem I had, and the only fix they could come up with was to have Grub2 on the physical drive with Windows.  I suppose if that's the only way it could possibly work, then I'd have to know how to do that (hopefully without completely re-installing Ubuntu).  But as I said, I'd like Grub2 on the Ubuntu drive if that is at all possible?

---

### Post by oldfred on 2011-11-01
When you boot from any other than the first drive that becomes hd0 with SATA drives. On my system I have had to manually edit entires as I boot any of 4 drives or even additional flash drives. My chain load to another MBR has to vary depending on drive booted. Boot drive is always hd0, but then the other drives seem to follow motherboard port order which matchs sda, sdb, sdc, sdd etc. But if I boot sdc, sda is then not hd0 but hd1.

Try adding a device map entry in the grub boot stanza. You can experiment with that. You could also add a chainload entry to 40_custom but again the drive may change. Usually the os-prober adds the drivemap command, so maybe they have changed something?

```
menuentry "Microsoft Windows 7" {
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 96161BAD161B8D7D
[COLOR=Red]drivemap -s (hd0) ${root}[/COLOR]
chainloader +1
}

```

Add this to 40_custom

```
menuentry "Windows on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

```

---

### Post by markjs on 2011-11-01
> **oldfred said:**
> When you boot from any other than the first drive that becomes hd0 with SATA drives. On my system I have had to manually edit entires as I boot any of 4 drives or even additional flash drives. My chain load to another MBR has to vary depending on drive booted. Boot drive is always hd0, but then the other drives seem to follow motherboard port order which matchs sda, sdb, sdc, sdd etc. But if I boot sdc, sda is then not hd0 but hd1.

Try adding a device map entry in the grub boot stanza. You can experiment with that. You could also add a chainload entry to 40_custom but again the drive may change. Usually the os-prober adds the drivemap command, so maybe they have changed something?

```
menuentry "Microsoft Windows 7" {
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 96161BAD161B8D7D
[COLOR=Red]drivemap -s (hd0) ${root}[/COLOR]
chainloader +1
}

```

Add this to 40_custom

```
menuentry "Windows on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

```

I put those two things in exactly as you had them and still exactly the same thing, when you boot from the 2nd drive (according to the printing on the motherboard itself, which is the Ubuntu one with grub2) and use the newly modified windows menu entry just black with flashing cursor.

I barely understand the syntax of the /boot/grub/grub.cfg file, but one thing I find puzzling, though I have no idea if it matters, is that if you look at the motherboard itself, you have in SATA1 the Windows drive, then in SATA2 the Ubuntu drive, and in SATA3 you have the OS X drive.

In /boot/grub/grub.cfg however, it shows the Windows drive labeled as "hd0" but I'd expect the ubuntu drive to either be "hd0" since it's set to boot first, or possibly "hd1" since it is in the second SATA port, but /boot/grub/grub.cfg names the Ubuntu (SATA2 plug) "hd2"?  For some reason, the Mac drive which is plugged into SATA3, comes up labeled "hd1"

This seems complicated to explain so bear with me please.  

I guess what I'm saying is I would expect it (/boot/grub/grub.cfg) to label according to where each is physically plugged in, or failing that, to label according to the order they are listed in the BIOS, the first being "hd0", then "hd1" and "hd2".  The thing is though, it has the first one plugged in (SATA1 on the board, but second in BIOS  the one with Win7) labeled "hd0" , then the second one, plugged into SATA2 on the board, but in first in BIOS (Ubunto with Grub2 on it) ends up labeled "hd2", with the third one (plugged into SATA3 and listed third in BIOS with OS X on it), gets labeled as "hd1" by /boot/grub/grub.conf.

So it seems most logical to me that it is mislabeling two of the drives, if not then all three.  Assuming they should be labeled by the order they are plugged in, then only the Windows drive is labeled right.  Assuming they should be labeled in order of how they list in BIOS, then all three would wrong? but yet, 

Both Ubuntu and Mac OS X boot fine, if booted from SATA2.  If you set SATA2 if it's set to boot first in BIOS, it's just the Windows menu entry that fails.  Respectively if you set SATA3 as first, Mac OS X boots, and if you set SATA1 you get windows with no problem, but the Windows drive will only boot into Windows.

Sorry I know it's confusing, but that's the best I can explain it, and still I'm stuck.

---

### Post by oldfred on 2011-11-01
It has always been confusing to me, and with a flash drive I had to try many hdX entries until I found one that worked.

I am not sure it is grub, but the BIOS. When in BIOS you select a drive to boot that is the first drive (old IDE nomenclature - primary master which my SATA system calls it, or boot drive). Grub then calls that hd0.

But when booting from hd1 then some BIOS info in memory is not consistent for Windows as Windows wants to be hd0. Generally the sudo update-grub reorders any info needed and it just works. But some BIOS/grub2/Windows combinations seem to have issues.

Did you try experimenting with different hdX numbers? Also edit out search line by UUID and just use hdX entry. X may be 0,1, or 2.

---

### Post by markjs on 2011-11-01
I've tried all kinds of experimenting with that changing the drive syntax in /boot/grub/grub.cfg manually and no matter what I name anything it acts exactly the same if I boot off that drive, I can only boot to Ubuntu or OS X.

So I'm tired of fooling with this; if anyone has an answer, I'd love to hear it but all this fumbling in the dark is a waste of time.  

As I said, I read another thread where the guy had the same problem and the only answer he could find that worked was to put Grub2 on the Windows 7 drive.  The reason I didn't want to do this was because Windows, should I need to re-install it would wipe out Grub2 and I'd lose access to Ubuntu (though I suppose I could always get it back with a live CD?).  

As it is set up now, (or how it would be if it worked right) if one OS got whacked, the other two would be fine.  If I move it to the Windows partition, should I have Windows problems, Ubuntu would lose the ability to boot, but since it seems the only way to get things working without having to go into the BIOS to choose my OS, I suppose my last question (barring someone coming up with an answer to the first one), is what do I have to do to remove install Grub2 to the Windows drive so I can boot any chosen OS WITHOUT having to re-install Ubuntu? (I am 99.9% sure if I do that it will sort itself properly since that's what the other guy ended up doing and it worked for him.)

I guess I could also ask, can I have Grub2 on both the Windows drive, AND the Ubuntu drive, then just edit out the Windows entry on the Ubuntu drive's copy of Grub2?  So that essentially to boot Ubuntu, I get one Grub menu with all three OS choices (from the Windows drive), then it proceeds to the Grub menu on the Ubuntu drive, where I can still choose from Ubuntu or OS X, but not Windows.  

Can that be done?  Reason for doing it that way being that all three drives could boot their own OS completely independently of even having the other two plugged in (sort of a roundabout way to get to my original desired goal.)

I guess the pitfall I see there is that when you do any operation with Grub2 thereafter, you'd have to make sure you were working on the right one, and it seems kind of mad and like that might not work either (assuming Ubuntu has some sort of thing like a Windows registry that only allows for one instance of Grub2).

This should theoretically solve itself, and I am 99% positive last time I had Ubuntu installed it worked fine without these problems, but not this time.  I'm tempted to just try installing Ubuntu fresh to just see if that would fix it, but if I did that, I'd still not know what went wrong.  Still having spent half the day on this I just want to to work and stop having to fight it!

---

### Post by Mark Phelps on 2011-11-01
> **markjs said:**
> Let me explain further.  I want the Windows, and the Mac drives to boot by themselves into their respective OSs with no bootloader on them, so that if you physically removed the rest of the drives it would be straight to the OS.

Regarding Windows, unless the boot loader is ALSO on the drive, and it is the only drive connected, I don't know how you could then boot into Windows.

I've heard that it might be possible to have the Windows boot loader on one drive and the actual OS on another, but I've not actually seen that work.

So, based on your statement above, what you want does not seem possible.

---

### Post by oldfred on 2011-11-01
You can install grub to as many drives as you want. I have most of my installs on sdc but also boot different installs in sdc from sda or sdb and from flash drives. For me I have different defaults in each MBR but modify 40_custom so when I forget to press f12 I can boot it from the menu, but my menus have gotten so long I prefer to use different MBRs.

A few users just install grub to a flash drive so then they do not have to modify Windows boot loader. But have Ubuntu on hard drive.

You could also create a small grub only boot partition to hold a grub.cfg file on the Windows drive. Then you should be able to boot that drive and boot the other drives. You have to manually create grub.cfg in a grub only boot partition, but can just copy the boot stanzas from other installs.

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)

---

### Post by oldfred on 2011-11-01
On Mark's post. We have seen a few cases where users installed Windows 7 in a second drive and Windows 7 put its boot files (the 100MB partition) on sda.

I was able with some effort to create a Windows 7 repair CD that booted with Windows 7. Then install grub2 over the top with the grub partition in the windows partition (issue is not to create two /boot folders) and use grub to boot. It chain loaded back to the PBR of the partition that the grub files are in. I was surprised it worked, but then I was able to use grub to boot other ISO repair distributions in another partition on the same flash drive.

---

### Post by markjs on 2011-11-01
> **Mark Phelps said:**
> Regarding Windows, unless the boot loader is ALSO on the drive, and it is the only drive connected, I don't know how you could then boot into Windows.

I've heard that it might be possible to have the Windows boot loader on one drive and the actual OS on another, but I've not actually seen that work.

So, based on your statement above, what you want does not seem possible.

I guess you need to read what I'm saying more carefully and maybe understand I am not an expert and may not get every technical term perfectly?

This is just infuriating and I don't know why it is so damn hard for me to be understood here!  Let me try to explain AGAIN!

What I want is my Windows drive to be TOTALLY UNMODIFIED!  Just the way WINDOWS built it.  Then I want my Mac drive to be EXACTLY like OS X made it.  Now maybe I used the term bootloader incorrectly?  Yes it has to have the Windows bootloader on the Windows drive, but I want Grub on the UBUNTU drive, so that if I ONLY plug the Windows drive in, it boots with no menus, just straight to Windows, which it does now.  Then if you put ONLY the Mac drive in, it boots to OS X with no menus.  Then the Ubuntu drive should have grub, and be able to boot into any of the other OSs.

I have had this setup before and it worked with no problems.  It should in theory work again but I can't for the life of me seem to get it to!

I did remember one detail that is different now than the last time I had a similar setup when it did work.  That time Ubuntu was installed from a CD and this time it was installed from a USB stick.  I'm thinking that has to be why because it's the only different variable, but then again why should it be different so long as that is unplugged?

This is a nightmare, because I have done exhaustive searching and sifting through totally irrelevant information (it seems quite a rarity that anyone uses separate physical drives so information on that is scarce), and so far all I've been able to find is other people with the same problem and no solutions.

---

### Post by oldfred on 2011-11-01
We have seen a lot of users boot Windows 7 with grub2 from another drive. Many boot scripts posted here.

Perhaps it is your BIOS. Is it up to date?

---

