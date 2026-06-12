---
title: "[also Windows and Ubuntu] Windows won't start/No startup repair/Reinstalling Ubuntu"
date: 2011-08-01
forum: General Help
---

### Post by Orangestar on 2011-08-01
Wow, I don't think that title could get any larger.

Oh right, whoops. I'm supposed to be serious. Well, I've been using Ubuntu since the very end of it's 10.10 era, after borrowing someone's installation disk to check if it worked. I fell in love and installed it on my HP G60 laptop. I installed Ubuntu 10.10 using Wubi, since I didn't realise that Ubuntu usernames had to be lowercase, and thought Ubiquity had crashed on me twice. I'm not making that mistake again.

I've used this computer for 3 years, and 25% of that has been with Ubuntu installed. Just recently, my computer crashed in Windows 7. I have been unable to boot into any user or even run startup repair. Even repair disks won't work. This makes a chkdsk out of the question.

Since I used Wubi, this means I can't use Ubuntu 11.04 either. So right now, I'm in that same 10.10 disk posting this. I'm finally fed up with this, and am planning to reinstall Ubuntu 10.10 on my Ubuntu Partition. Now on to my questions:

1) Would formatting the partition and then reinstalling Ubuntu do something bad to my Windows partition, since I used Wubi? Is there any way to uninstall Wubi using the CD?
[color=blue]A) No, it will not ruin windows. No, you cannot uninstall Wubi with the CD.[/color]

2) Can I use "Check" in GParted as a replacement for Chkdsk /f?
[color=blue]A) No, you cannot.[/color]

3) Is there any other boot CD I can use to run Chkdsk? I've tried Memtest86+, HP's pre-installed boot stuff either didn't work or wouldn't show up, and like I said, repair disks seem to do no good.

---

### Post by Theredbaron1834 on 2011-08-01
I wish I could be of more help, but I don't think you are in luck. It sounds pretty bad, but I will try.

1. I don't think that will do anything. It might leave a leftover boot option in the windows boot screen, but since you would be replacing it with grub2 anyways, I don't see a problem.

2. Nope, fraid not. Trust me, I tried. I had a 320gb ntfs ext drive. It farked, wouldn't even mount in linux anymore. And crappy me without a dos to boot. Sucked. 

3. A BartPE might work, but I really don't know. Never tried it myself, but it seems that it is in the bartpe disk creation thing, so it should work.  You could also try [this]("http://thecomputerparamedic.com/index.php?option=com_content&view=category&layout=blog&id=16&Itemid=29"). Again, I never tried it, but it is the recovery console on cd.

Good luck.

---

### Post by Mark Phelps on 2011-08-01
> **Orangestar said:**
> 1) Would formatting the partition and then reinstalling Ubuntu do something bad to my Windows partition, since I used Wubi? 
Formatting the Windows partition will erase Wubi.  I that your question?

> Is there any way to uninstall Wubi using the CD?Nope -- it's installed like a Windows app.  You have to uninstall it inside the WORKING Win7 install.

> 2) Can I use "Check" in GParted as a replacement for Chkdsk /f?
Nope -- you could TRY using ntfsfix -- but that only repairs some trivial NTFS problems.

> 3) Is there any other boot CD I can use to run Chkdsk? I've tried Memtest86+, HP's pre-installed boot stuff either didn't work or wouldn't show up, and like I said, repair disks seem to do no good.
You could Google for Hiren's Boot Disk.  It contains LOTS of utilities.  Perhaps one or more of them could repair your NTFS partitions.

---

### Post by Orangestar on 2011-08-01
> **Theredbaron1834 said:**
> And crappy me without a dos to boot.
Wait, I've still got an old DOS disk, could I run chkdsk from there?

> **Mark Phelps said:**
> Formatting the Windows partition will erase Wubi.  I that your question?
Sorry, I meant formatting the UBUNTU partition.

---

### Post by Theredbaron1834 on 2011-08-01
Sorry, I ment dows, no idea why I said dos, guess I was more tired then I felt.

I think you should try that recovery console disk. It is less then 8mb in size, so even on dialup it won't take long to get.

O, and I didn't know wubi used partition's. I thought it was a loop file on the windows partition. So I really don't know much about that.

---

### Post by Orangestar on 2011-08-01
> **Theredbaron1834 said:**
> 
O, and I didn't know wubi used partition's. I thought it was a loop file on the windows partition. So I really don't know much about that.

I'm not all too sure myself... None of these seem like Ubuntu...

[img]http://i.imgur.com/v4rD4.png[/img]

---

### Post by Theredbaron1834 on 2011-08-01
None of those are a nix system. Ubuntu defults to ext4, though ext2 might be a better filesystem for a dual boot system. NTFS is a Windows only thing really.

This is weird, according to the boot loader sda1 is Win7, sda2 has no os, and sda3 is Vista. The problem is that there is NO way sda1 is win7, as there is no where near enough space.

Can you mount the first or second partition? What error happens when you try? When you mount the third, can you access the files, can you see a windows folder?

From the command line type
```

sudo mkdir /tmp/windows
sudo mount /dev/sda1 /tmp/windows/

```and paste the output.
if it does mount you can unmount with
```
sudo umount /dev/sda1 /tmp/windows
```and remove folder with 
alt+f2 and typing gksu nautilus, and going to /tmp/ and deleting windows

And do the same with sda2 instead of sda1 too. As well as sda3 if it doesn't mount in the file browser.

---

### Post by Orangestar on 2011-08-01
Crap, I'm really confused now.

Anyway, I was able to successfully mount sda1 and sda3. Here's the terminal output:

```
ubuntu@ubuntu:~$ sudo mkdir /tmp/windows
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /tmp/windows/
ubuntu@ubuntu:~$ sudo mkdir /tmp/sda2
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /tmp/sda2/
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read vcn 0x8: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ubuntu@ubuntu:~$ sudo mkdir /tmp/sda3
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /tmp/sda3/

```

Heres a screenshot of the drives in nautilus

[sda1](http://i.imgur.com/F0sNJ.png) and [sda3](http://i.imgur.com/23Ljl.png)

---

### Post by Theredbaron1834 on 2011-08-01
Ok, so I still have no idea what the first partition is. The third is a recovery partition. Do you have an extra 4gb flashdrive, ect you could use? If so I would install ubuntu, or somekinda nix that uses grub2. When it installs it should find the recovery partition, and let you boot to it. From there you can restore your windows. The only problem is that it will most likely remove all your files.

Did you try and boot that Recovery console CD? If you have any files you want to keep, I say that is your best bet.

Do you have another computer, or a friend that will let you use it? Cause if so you can hook up your hard drive to it, and boot it's/his/her computer and run chkdsk from it.


So,
SDA1=unknow
SDA2=Your Windows partition. /Le screwed
SDA3=Your recovery partition.

Now at least we know what is what.

---

### Post by Orangestar on 2011-08-01
Okay, good.
No, I haven't tried that recovery disk you showed me, mostly because it said "Windows **XP** Recovery disk." I've been able to use the Grub console to boot into the recovery partition, but it didn't give me any options to fix anything. (IE,[COLOR=blue]_ [this]("http://cybernetnews.com/wp-content/uploads/2009/10/windows-7-recovery-disc-1.png") _[/COLOR]wouldn't come up. At all.) Not even recovery disks would work.

I do have another laptop that is the exact same model. It's my brothers. However, I'm kinda worried about unscrewing the bolts on my laptop. :(

[s]Also I'm pretty sure the first is Ubuntu. When I looked at Gparted, it said "SYSTEM", which is what the file system said on Ubuntu.[/s] Forget that, I don't know what I'm talking about.

---

### Post by Theredbaron1834 on 2011-08-01
Can you give a pic of what does come up? I don't care if it is with a crappy camera phone, any pic that lets me see it would help.


O, laptop yeah, I can see why you would be worried. First time I cracked my case open, I was scared big time I would be able to get it back. I may do it all the time now, to do this, that, and the other thing, but still sometimes scared.

It doesn't matter what recovery disk it is. You aren't going to recover the windows, per say. It lets you boot to a recovery console, IE a command line that lets you run chkdsk, among other things. Won't fix a virus problem, or much else really, but chkdsk should work.

And don't worry. Most normal users don't really know/care what a linux filesystem looks like, long as it works. So not knowing isn't a big deal. A easy way to tell is that ubuntu is a big distro, and ther is no way a graphic desktop of ubuntu will fit on less then, 2gb. And at only 208 mb, no way. Maybe a puppy linux variant, DSL, tinycore, but not ubuntu.

---

### Post by Orangestar on 2011-08-01
> **Theredbaron1834 said:**
> Can you give a pic of what does come up? I don't care if it is with a crappy camera phone, any pic that lets me see it would help.
It's just the background. No windows or anything.

> **Theredbaron1834 said:**
> 
It doesn't matter what recovery disk it is. You aren't going to recover the windows, per say. It lets you boot to a recovery console, IE a command line that lets you run chkdsk, among other things. Won't fix a virus problem, or much else really, but chkdsk should work.
That's, actually, that's pretty much what I was looking for! Neat! guess I will be trying it out.

EDIT:
> It's not much use on modern computers with sata drives as it does not include the drivers for such devices, but people all over the world download daily through copied links.
I'm not much of a geek on hard drives, but doesn't SDA mean a SATA hard drive?

---

### Post by oldfred on 2011-08-01
Windows 7 installs to two partitions. The first is boot/recovery and is typically 200MB system partition. The main install it the other partition. You can supposedly get into the repair on the system by hitting f8 as it boots, but with grub the timing is difficult. You have to hit f8 after grub but before windows. some said it takes many tries.

---

### Post by Theredbaron1834 on 2011-08-01
Well, that sucks. Maybe it is messed too then. :(

That's good to know oldfred. Didn't know that it could do that. I tried Win7 twice so far, and it was just the partition I told it to use. I like that way better though. Glad that windows finally went the nix way and let the boot partition be sep from the booted partition.

No, it is diferent depending on the kernel you use, but I think modern kernels use sdX for all read/write drives. My sata/ide/sd/usb drives are all some version of sdX. I don't know how to tell if you use sata or ide from Ubuntu. If you works, it works, if not, then I guess you will know. Only cost a cd-r to find out, or an rw.

---

### Post by oldfred on 2011-08-01
You can use any windows repair CD to run chkdsk.

But a Vista/7 CD will not auto  repair XP like it can with Vista or 7. You can run some commands to fix some things in XP from a Vista or 7 CD.

Lets see what is installed where from Ubuntu or LiveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Orangestar on 2011-08-01
Heh, I'm no stranger to BBcode. I manually type this stuff out.
To reiterate, I HAVE tried booting into repair mode with F8. Gave me a blank screen.

Anyway, on to the ```
 tags.

[code]
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   463,431,678   463,022,079   7 NTFS / exFAT / HPFS
/dev/sda3         463,431,680   488,394,751    24,963,072   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2064B79D64B773DE                       ntfs       SYSTEM
/dev/sda2        8A784F7A784F6453                       ntfs       
/dev/sda3        0A527DAF527DA05D                       ntfs       RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /tmp/windows             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /tmp/sda3                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-10-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=8A784F7A784F6453 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-10-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-10-generic root=UUID=8A784F7A784F6453 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-10-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=8A784F7A784F6453 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=8A784F7A784F6453 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=8A784F7A784F6453 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=8A784F7A784F6453 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 2064B79D64B773DE
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 8A784F7A784F6453
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 0A527DAF527DA05D
    drivemap -s (hd0) ${root}
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

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  14.591548920 = 15.667556352   boot/grub/grub.cfg                             1
  13.031250000 = 13.992198144   boot/initrd.img-2.6.35-28-generic              2
   7.596801758 = 8.157003776    boot/initrd.img-2.6.38-10-generic              4
  14.699470520 = 15.783436288   boot/initrd.img-2.6.38-8-generic               2
  10.597751617 = 11.379249152   boot/vmlinuz-2.6.35-28-generic                 1
   3.504215240 = 3.762622464    boot/vmlinuz-2.6.38-10-generic                 2
  13.058898926 = 14.021885952   boot/vmlinuz-2.6.38-8-generic                  1
   7.596801758 = 8.157003776    initrd.img                                     4
  14.699470520 = 15.783436288   initrd.img.old                                 2
   3.504215240 = 3.762622464    vmlinuz                                        2
  13.058898926 = 14.021885952   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

ls: reading directory sda2/: Input/output error

```

---

### Post by Theredbaron1834 on 2011-08-01
I don't know much about bootinfoscript.

However, from what I can tell, your files are still there. It is just a matter that it can't be mounted. Leaves me to believe that it just needs chkdsk to be run. 

But let us see what fred says about it.

---

### Post by Orangestar on 2011-08-01
I'd like to add that I tried your XP recovery disk.

Gave me a BSOD.

---

### Post by Theredbaron1834 on 2011-08-01
That really sucks. Trying to save your data, but it might not be possible. 

Did you try a bartpe disk? That is the last idea I have on saving your data. After that, you might have to reformat. :(

---

### Post by oldfred on 2011-08-01
It looks like you have the full set of boot files in sda2, but are still set to boot from the boot/recovery in sda1. You could try moving the boot flag with gparted from Ubuntu disk to sda2 and see if that makes any difference.

But this concerns me at end of script

> ls: reading directory sda2/: Input/output error

But it did mount sda2 adn show windows files in the partition.

---

### Post by Theredbaron1834 on 2011-08-01
Yeah, I was confused by that too. How could it see that the files were there, if it had an in/out error. I was hoping you would have an idea. Guess it is one of those unknown unknown's.

---

### Post by Orangestar on 2011-08-02
Well that really sucks. No, I haven't tried a BartPE yet, but I need my brother's approval before I can use his computer. :(

At any rate, the answer seems to be either slowly taking form, or slowly rushing away from us.

---

### Post by Theredbaron1834 on 2011-08-03
Well, best of luck with that. I hope you have a nice brother. :)

Yeah, I really hate ntfs. I sometimes dualboot xp, for games. But I always use fat32. Ntfs is just to problematic, and can only be fixed by windows. I learned my lesson from my ext drive. I know you pretty much have to use ntfs for win7, but I hate 7, so it doesn't bother me. 

Do you have your cd key, should be either on a sticker on your lappy, on the recovery cd that came with it, or maybe in the paperwork. Might not be able to save your data, but I would hope to at least save your ability to use windows. Unless you have said CD key, there is no legal way for you to keep using windows, ie a reinstall. Another prob with windows is that after something like this happens, even though you do have a legal right to it, you can't reinstall windows. Do to a lost/faded, or in some cases never received cd key. I have the right to 4 windows installation's, but like I can find the cd key anymore. Said, but if I want to get windows, I have to pay for it. But you can't really buy an XP new anymore I don't think. And my eee doesn't support anything past XP. Can get vista and 7 to run, but the drivers are default, ect. Can't play any games on 7 either, as the graphics driver sucks.

---

