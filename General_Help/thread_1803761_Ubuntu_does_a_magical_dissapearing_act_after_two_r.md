---
title: "Ubuntu does a magical dissapearing act after two reboots."
date: 2011-07-13
forum: General Help
---

### Post by The_supreme_penguin on 2011-07-13
This awesome penguin needs help. The title pretty much says it all. At the link below,

[http://forums.novell.com/suse/suse-product-discussion-forums/suse-linux-enterprise/suse-linux-enterprise-server-sles/sles-hardware/385137-partition-disappears-gtp-disk-after-two-reboots.html]("http://forums.novell.com/suse/suse-product-discussion-forums/suse-linux-enterprise/suse-linux-enterprise-server-sles/sles-hardware/385137-partition-disappears-gtp-disk-after-two-reboots.html")

I found someone with the same problem. The solution was to disable the Zenworks Linux Management client. I just installed natty narwhal! Did it come with Ubuntu 11.04 (Natty narwhal) and how do i disable it.

Please? I am the supreme penguin. You must answer to me.

Please read the link before replying. It pretty much the same problem as me. And if you want any more info i can give it to you.

---

### Post by The_supreme_penguin on 2011-07-13
No i seriously need help.

---

### Post by The_supreme_penguin on 2011-07-14
Please help me.
Ive been putting Ubuntu on lock mode so it doesnt shut down and i dont have to reinstall it again.
But nobodys answering.
I need to know how to fix this!

---

### Post by The_supreme_penguin on 2011-07-14
IF I DONT FIND A WAY TO FIX THIS, I CANT USE UBUNTU AT ALL. BEING FORCED TO LEAVE AFTER TWO REBOOTS _SUCKS._ SOMEONE PLEASE HELP ME. IVE HAD TO KEEP MY COMPUTER ON ALL THIS TIME SO UBUNTU DIDNT SHUT DOWN.

EVERYONE ELSE GETS ANSWERS TO THEIR QUESTIONS. ANYBODY HAVE ANY ANSWERS FOR ME?

im sorry i sound rube but im losing patience. i ask a simple question and no one can help. im sure SOMEONE out there can help! i am reallllllly ticked off right now. its like im being shunned or something.
Here are some stats:
Acer aspire 5720z
Intel Pentium dual core 1.7 ghz
2gb ddr2 RAM
Windows 7 AND Ubuntu Natty Narwhal (11.04)
FUN FACT: My windows 7 desktop completely reset it self and i cant change it back to normal now. IT LOOK LIKE FREAKIN WINDOWS 98. May or may not be related. I think it is though.

---

### Post by oldfred on 2011-07-14
As far as I know Zenworks is not part of the standard Ubuntu install. Did you separately download and install it. Or is that what you think may be causing the problem?

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by The_supreme_penguin on 2011-07-14
Hi
Sorry for the wait. Been busy [playing minecraft].

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/bcd

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000175828992 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953468416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,743,753,215 1,743,751,168   7 NTFS / exFAT / HPFS
/dev/sda2       1,743,755,262 1,929,302,015   185,546,754   5 Extended
/dev/sda5       1,925,130,240 1,929,302,015     4,171,776  82 Linux swap / Solaris
/dev/sda6       1,743,755,264 1,920,958,463   177,203,200  83 Linux
/dev/sda7       1,920,960,512 1,925,117,951     4,157,440  82 Linux swap / Solaris
/dev/sda3       1,929,302,016 1,953,466,367    24,164,352  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    24,563,384    24,563,322  12 Compaq diagnostics
/dev/sdb2    *     24,563,712   488,392,703   463,828,992   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        54E06FBFE06FA5C8                       ntfs       My Passport
/dev/sda6        094fe87c-af25-4982-96e5-a2d06ac6e9bd   ext4       
/dev/sda7        db44ad10-72c2-4868-8705-3e90d01579d7   swap       
/dev/sdb1        48E09936E49BED2A                       ntfs       PQSERVICE
/dev/sdb2        82902AA5902A9FA1                       ntfs       Main Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/My Passport       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/Main Drive        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=094fe87c-af25-4982-96e5-a2d06ac6e9bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=094fe87c-af25-4982-96e5-a2d06ac6e9bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=094fe87c-af25-4982-96e5-a2d06ac6e9bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=094fe87c-af25-4982-96e5-a2d06ac6e9bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 094fe87c-af25-4982-96e5-a2d06ac6e9bd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 48E09936E49BED2A
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos2)'
	search --no-floppy --fs-uuid --set=root 82902AA5902A9FA1
	chainloader +1
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=094fe87c-af25-4982-96e5-a2d06ac6e9bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=db44ad10-72c2-4868-8705-3e90d01579d7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 911.621337891 = 978.845958144  boot/grub/core.img                             1
 875.773365021 = 940.354490368  boot/grub/grub.cfg                             1
 833.366458893 = 894.820421632  boot/initrd.img-2.6.38-10-generic              2
 832.698242188 = 894.102929408  boot/initrd.img-2.6.38-8-generic               2
 832.413394928 = 893.797076992  boot/vmlinuz-2.6.38-10-generic                 2
 911.619609833 = 978.844102656  boot/vmlinuz-2.6.38-8-generic                  1
 833.366458893 = 894.820421632  initrd.img                                     2
 832.698242188 = 894.102929408  initrd.img.old                                 2
 832.413394928 = 893.797076992  vmlinuz                                        2
 911.619609833 = 978.844102656  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

There you go.

---

### Post by oldfred on 2011-07-14
Nothing major out of place that I can see. You have extra swaps and the script does not mount them like the swap in sda7 which seems to be the one you are using. I would delete sda5 & sda3 unless you know there really are something else and have data you want to recover.

Your passport seems to be mounting as sda. Is not that the external drive and sdb is the internal? That is a bit unusual and may cause issues with windows as it may want to be the first drive. But all of that is controled by the BIOS not either system. perhaps something that thinks it is sda, is writing into sda which now is a different drive and corrupting data?

Are you running any proprietary software in Windows that uses DRM. That sometimes writes data in unusual places to hide serial numbers or other info.

---

### Post by The_supreme_penguin on 2011-07-15
> **oldfred said:**
> Nothing major out of place that I can see. You have extra swaps and the script does not mount them like the swap in sda7 which seems to be the one you are using. I would delete sda5 & sda3 unless you know there really are something else and have data you want to recover.

Your passport seems to be mounting as sda. Is not that the external drive and sdb is the internal? That is a bit unusual and may cause issues with windows as it may want to be the first drive. But all of that is controled by the BIOS not either system. perhaps something that thinks it is sda, is writing into sda which now is a different drive and corrupting data?

Are you running any proprietary software in Windows that uses DRM. That sometimes writes data in unusual places to hide serial numbers or other info.

The extra swaps are probably because i kept having to reinstall ubuntu. Ill use the ubuntu CD to get rid of those...

Im not sure which is sda and which is sdb but your right it does sound like my passport is sda which is odd...

Proprietary DRM software? [ That sounds like steam.]("http://store.steampowered.com") I have way too may games on steam.

---

### Post by NERDMAN! on 2011-07-15
i cant really help with your ubuntu dissappearing act but i can tell you the reason why windows looks like win98 is because its somehow decided to revert to total performance settings. i dont know where the settings dialog in win7 is but in xp its found under control panel> system> advanced> performance options.
all you should need to do is re enable all the visual effects.
if that doesnt fix it or if they are already enabled then i would say you have an issue beyond simple configuration. wish i could help with ubuntu, perhaps if your passport is being mounted as sda, and assuming you installed ubuntu on a separate device altogether, my first thought would be remove the passport and reboot the pc. otherwise check the boot order in bios.
i doubt steam would be writing to a swap partition, it is likely the number of reinstalls. also it may be an idea to downgrade to 10.04 LTS as 11.04 natty is known for its issues with unity. :D


and good on ya for playin minecraft. pm me sometime and i'll give ya the ip for my server :D
and also i know how it feels to be waiting forever for a reply, (still waiting on help with my KQ audio issues)
sorry we couldnt help ya out sooner :(

regards
NERDMAN!

---

### Post by The_supreme_penguin on 2011-07-15
Ok thanks for the help with Windows 7. ONLY PROBLEM...Ive already accidentally shut dow my computer once. If i do it again, Ill have to COMPLETELY REINSTALL UBUNTU. Ive been keeping it on lock screen whe im not using it and im scared it has an auto-shoutdown setting. So, i cant go and fix that while in ubuntu...But when i do get out of here alive Ill be sure to fix that so thank you.

:popcorn: (no clue what this has to do with ubuntu but i put it there because i felt like it)

---

### Post by NERDMAN! on 2011-07-15
> **The_supreme_penguin said:**
> Ok thanks for the help with Windows 7. ONLY PROBLEM...Ive already accidentally shut dow my computer once. If i do it again, Ill have to COMPLETELY REINSTALL UBUNTU. Ive been keeping it on lock screen whe im not using it and im scared it has an auto-shoutdown setting. So, i cant go and fix that while in ubuntu...But when i do get out of here alive Ill be sure to fix that so thank you.

:popcorn: (no clue what this has to do with ubuntu but i put it there because i felt like it)

ive not heard of ubuntu having an autoshutdown but it is a valid fear, i'll look into that for ya, least i can do is try to save ya a bit of worry.

edit: i couldnt find anything remotely like an autoshutdown in ubuntu by default. while i am positive theres packages available that do it, ubuntu doesnt come with any by default. but it still makes good practice to check your power management settings and make sure it doesnt hibernate or suspend automatically.

---

### Post by DawieS on 2011-07-15
> **The_supreme_penguin said:**
> 
I found someone with the same problem. The solution was to disable the Zenworks Linux Management client. I just installed natty narwhal! Did it come with Ubuntu 11.04 (Natty narwhal) and how do i disable it.

So, did you have **Zenworks Linux Management** installed, and have now disabled it? And it fixed your problem?

If not, then I have a strong suspicion that a possible bug in **Power Manager** causes this behaviour. I had the experience that while doing a copy from one disk to another, all partitions on the source disk was marked as "dirty", and the disk was off-lined (**Power Manager** was also involved, for more information, see [_**this post**_]("http://ubuntuforums.org/showpost.php?p=11044160&postcount=65")). Now if your Ubuntu installation was on this off-lined disk, you would not be able to boot from it, since all partitions would appear to be empty. However, it is not required to re-install Ubuntu, all you need to do is boot from another working copy of Ubuntu, or Live CD, and run a **Check Filesystem** from the **Disk Utility**, to restore your partitions. (I had to switch the drive off, and back on, to be able to see it). You will then be able to boot from it.

A work-around is to disable the **Power Manager** daemon at** System** > **Preferences** > **Startup Applications** (In 10.04). You will obviously not be able to spin-down disks, or hibernate. Your screen saver will still work though.

---

### Post by linuxuser12345 on 2011-07-15
No one is going to want to help you when you say "I am the supreme penguin. You must answer to me." I know you meant it as a joke and all, but things like that may make people not want to help you

---

### Post by The_supreme_penguin on 2011-07-15
> **DawieS said:**
> So, did you have **Zenworks Linux Management** installed, and have now disabled it? And it fixed your problem?

If not, then I have a strong suspicion that a possible bug in **Power Manager** causes this behaviour. I had the experience that while doing a copy from one disk to another, all partitions on the source disk was marked as "dirty", and the disk was off-lined (**Power Manager** was also involved, for more information, see [_**this post**_]("http://ubuntuforums.org/showpost.php?p=11044160&postcount=65")). Now if your Ubuntu installation was on this off-lined disk, you would not be able to boot from it, since all partitions would appear to be empty. However, it is not required to re-install Ubuntu, all you need to do is boot from another working copy of Ubuntu, or Live CD, and run a **Check Filesystem** from the **Disk Utility**, to restore your partitions. (I had to switch the drive off, and back on, to be able to see it). You will then be able to boot from it.

A work-around is to disable the **Power Manager** daemon at** System** > **Preferences** > **Startup Applications** (In 10.04). You will obviously not be able to spin-down disks, or hibernate. Your screen saver will still work though.

See i have no clue if ZENWorks Linux management comes with linux. I though maybe it came with ubuntu and i wanted to know if there is anyway to disable IF THAT IS THE CASE.

It seems it isn't.

About the "All you would need to do is use Live CD to check filesystem", I am a complete moron. So thanks for that...

Ill try disabling the power manager, but will i be able to lock screen? I end up doing that a lot. Although i dont hibernate a lot and i have no clue what spin-down means.

As for the post above this well sorry. It was a joke. Didnt mean to be rude. If you want i can find a way to change my name.

EDIT: IT DIDNT WORK O NOES!!

---

### Post by The_supreme_penguin on 2011-07-16
IT DIDNT WORK.

I shut down crossing my fingers but sure enough i could not boot from that partition.

NOW FOR THE WEIRDNESS!!

A) Windows 7 completely back to how i had left it. (as in, completely back to normal, even though i didnt change a thing.) Definetly confirms my suspicions that they were connected. Maybe.
B) Ubuntu Live CD Filesystem check comes up clean.
C)  On a whim, i checked what the SMART data for the disk said. Current Pending Sector Count (197) had a WARNING light on. The first two lights were good, and the rest of the lights were N/A. Again, not sure what this could mean.

Typing this from the live CD now. Not sure what my next step should be.

---

### Post by DawieS on 2011-07-16
> **The_supreme_penguin said:**
> 
Typing this from the live CD now. Not sure what my next step should be.
Are your backups up to date?

---

### Post by DawieS on 2011-07-16
> **The_supreme_penguin said:**
> 
I shut down crossing my fingers but sure enough i could not boot from that partition.

Also, you will have to be more specific if you expect meaningful advice.

Did you get past the Grub menu?
What was the error messages/symptoms?

---

### Post by The_supreme_penguin on 2011-07-16
Sorry wasn't very specific as to how i boot into Linux. Here's exactly how I boot into it: 

step 1) as my computer is booting,I have it set to allow me to bring up a boot menu so as to what to boot first. This is where my problem lies. When Linux is installed, the first two times Linux appears on the list, along with something else (I am assuming it is the recovery partition.) when ubuntu disappears, all I get is the three normal options (which I still have even when linux is installed) my main drive, which boots into windows 7, my cd drive, which if I have a bootable cd I boot into that, and network boot. Not sure whAt that is never risked it. 

Step 2 if I boot into ubuntu is GRUB. I get ubuntu, ubuntu recovery, windows 7, a windows vista recovery partition, and memtest 86+ or something. Then I boot into ubuntu. Hopes this helps.

---

### Post by oldfred on 2011-07-16
Are you using BIOS to boot every time and not just setting it to boot sda or your 1TB drive? I do not know if BIOS would see systems just drives or is it something your PC vendor has added?

---

### Post by The_supreme_penguin on 2011-07-17
Yepity I boot from BIOS.

Ok, but i must confess, MORE WEIRDNESS JUST HAPPENED and now i am back in ubuntu with no idea how i got here.

EXACTLY WHAT HAPPENED:

step 1) I boot my computer into windows 7. It boots, and as it says Please wait with that little hynotizing circle, It goes to preparing to configure windows, then configuring windows (0% complete, 100% complete). I think, Ok, Windows update is updating my computer.

step 2) It shuts down. I go WHAT THE-

step 3) It boots up again. Im glad my computer is not totally brain dead.

step 4) After a very long and boring black screen (after the BIOS, which is when i normally boot into Ubuntu), **_GRUB COMES ONTO MY SCREEN, PURPLENESS AND ALL._**

step 5) Ubuntu is still there, so i select it.

WHAT JUST HAPPENED?!?!

Im glad and all, but now i am REALLLLLLLLY confused. I dont THINK i installed GRUB to the master boot record! I dont know WHERE Linux installed it! This is so totally odd.

---

### Post by oldfred on 2011-07-17
Going back to boot script. You have grub install to both MBRs.

I also did now notice in one place it shows sdb2 as  NTFS which is correct but partition table shows it as FAT16. You need to correct that which may be what windows was doing. Also was windows originally sda of the first disk and you added the 1TB and now it is the first drive? Windows does not like that and has to have the BCD updated to know it is the second drive. Perhaps that was what it was doing.

Reboot with grub in the MBR should just boot automatically to Ubuntu. But it should also show the menu with a windows entry.

---

### Post by The_supreme_penguin on 2011-07-18
Well every since exiting ubuntu, Whenever i boot windows there is no ubuntu entry in the BIOS and also windows will ALWAYS boot saying "applying update operation..." (like when i explained that the update shut down my computer and brought me to GRUB,) except it doesnt shut down! So now have absolutely no clue what to do next.

Questions)

1) Where is Grub? Should i reinstall it thru windows? Should I just get another bootloader? Or is it even GRUBS fault?
2) Whose fault is it? Windows or ubuntu or BIOS or GRUB?
3) How do i correct this problem? (This is the most important one.)
4) Why me? :mad:

---

### Post by oldfred on 2011-07-18
BIOS and operating systems are two different things. BIOS does not see an operating system. BIOS just jumps to the MBR of a bootable device and starts the process of loading that code. Since MBR is tiny it usually just then jumps to more code to load from somewhere else on drive.

Windows standard boot loader will never show Ubuntu unless using wubi. You can install third party windows boot loaders that will also boot Ubuntu. 

Did you fix the partition error on sdb2? You may just need to use Disk Utility in System, Administration and select sdb2 and change it to 07 or whatever it sees for NTFS.

I would keep grub2's boot loader in sda and install a windows boot loader in the 250GB drive. 

Part of you problem still may be if windows was the first drive and now it is the second. Windows can work from the second but works much better if it is the first drive or sda. That usually is set just by which port you have which drive plugged into on the motherboard.

---

### Post by The_supreme_penguin on 2011-07-21
I think perhaps Ill just downgrade Ubuntu to 10.10. I wont ask for anymore posts here unless you think you know you have the answer. Thank for all your help everyone.

---

### Post by oldfred on 2011-07-22
If  you are going to reconfigue it is often better to make windows the sda drive. That is usually just controlled by which SATA port you have it plugged into or make it the lower number port.

---

