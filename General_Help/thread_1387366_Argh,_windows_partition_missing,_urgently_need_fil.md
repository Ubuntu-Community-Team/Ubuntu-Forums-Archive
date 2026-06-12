---
title: "Argh, windows partition missing, urgently need files perhaps turned into swap?"
date: 2010-01-21
forum: General Help
---

### Post by DiegoDeEscocia on 2010-01-21
Help all!

I've got a nightmare of a problem....I have an essay urgently due which is on my windows NTFS partition's my documents....


Somehow my windows partition seems to have disappeared. Selecting it at grub leads to a blinking cursor. I have observed that it nolonger appears under places in ubuntu....

I started Gparted and found a clue....it now reads /dev/sda1 (which is windows) linux-swap .....but boot is still selected.

I think it may be connected with having put my laptop into hibernate a week or so ago (haven't rebooted since then) after following this tutorial:

[http://ubuntuforums.org/showthread.php?t=395435](http://ubuntuforums.org/showthread.php?t=395435)

I removed the USB pen drive when packing it up and forgot to reconnect it on reboot....Could this be it?

How do I undo this? please tell me it's possible...even if only partial data recovery I really really need that essay....This is an absolute nightmare!

---

### Post by michy99 on 2010-01-21
What do you get for```
sudo fdisk -l
```

---

### Post by DiegoDeEscocia on 2010-01-21
```
Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4516    36274738+   7  HPFS/NTFS
/dev/sda3            4517        7296    22330350    5  Extendida
/dev/sda5            7027        7296     2168743+  82  Linux swap / Solaris
/dev/sda6            4517        7026    20161512   83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
1 cabezas, 63 sectores/pista, 31008336 cilindros
Unidades = cilindros de 63 * 512 = 32256 bytes
Identificador de disco: 0x0270a85a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           2    31008256   976760032+   7  HPFS/NTFS
```Thanks for your help! I get what I've pasted above!

Sorry my system is running in spanish I forgot to say :-/ does it make sense? or should I try changing it back to english?

---

### Post by synapsys on 2010-01-21
Can you mount it manually?

```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows

```

---

### Post by michy99 on 2010-01-21
It looks like Windows is still on sda1. What version of Ubuntu are you running and what do you get for```
grub-install -v
```

---

### Post by DiegoDeEscocia on 2010-01-21
That's a relief

in reverse order:

Grub install -v returns:
```

grub-install (GNU GRUB 1.97~beta4)
```And the attempt to manually mount it returns:

```
sudo mount /dev/sda1 /media/windows
mount: debe especificar el tipo de sistema de ficheros
```Which means:

Mount: You must/ought to specify the type of fileing system

...

PS- and ubuntu 9.10 Karmic Koala with all updates as of the day before yesterday :-)

---

### Post by michy99 on 2010-01-21
What happens if you enter```
sudo update-grub
```

---

### Post by DiegoDeEscocia on 2010-01-21
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: no se puede acceder a /media/Expansion: No existe el fichero ó directorio
done
```Don't worry about the last line - media/expansion is my external hard-disk...Doesn't look like windows is on the list....

---

### Post by michy99 on 2010-01-21
If you go to Places->Computer can you see your Windows partition? If so can you open it and read the files?

---

### Post by DiegoDeEscocia on 2010-01-21
Nope, that was one of the first symptoms I noticed.

All that appears now is my external HD, my CD rom drive and the ubuntu filesystem....I used to have a seperate volume in there for my windows drive....

Were I able to read the files that would solve the urgent problem - that's to say submitting my essay....

---

### Post by sailthesea on 2010-01-21
> **DiegoDeEscocia said:**
> Nope, that was one of the first symptoms I noticed.

All that appears now is my external HD, my CD rom drive and the ubuntu filesystem....I used to have a seperate volume in there for my windows drive....

Were I able to read the files that would solve the urgent problem - that's to say submitting my essay....

 Do you have a LiveCD to hand? You should at least then be able to boot a Live session and and copy the files to your external drive or USB device and get your paper in! It looks a bit like you have some of your wanted files on an extended partition which you can't mount whilst running the HDD 
 Just a thought anyway!:)

Edit : This is as per my limited Spanish!

---

### Post by michy99 on 2010-01-21
See if this will mount it.
```
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```

---

### Post by DiegoDeEscocia on 2010-01-21
I don't understand why the live CD will help?

Ubuntu is running from a different partition of the same HD as windows ought to be sitting on....windows being the first one (and where I actually think grub is running from....yet it won't boot??? and I'm not sure of this fact).

Ignore the 'extended drive' it's confusing the situation - it's my 1 terabite external for movies etc. It doesn't actually have my docs on it....

Why should I be unable to mount windows from ubuntu when running normally? I used to be able to???

Anyway I'm open to any suggestion that'll let me get at my windows files as it's pretty urgent :-/

I originally thought it must be something screwed up with the windows boot sequence until I saw that Gparted seemed to think the windows drive was swap.....

And I still don't understand why ubuntu doesn't seem to give the option to mount it......

I'm not sure if I've a live CD to hand I'd need to search for what I've done with it. I do have an ISO image of ubuntu 9.10 on the external drive so I suppose I could burn one.

---

### Post by DiegoDeEscocia on 2010-01-21
> **michy99 said:**
> See if this will mount it.
```
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```

You're a genius that worked... I can now access the files. Urgent side of the problem solved.

Not sure what I'll do about actually getting windows working again but at the very least I can copy the files I need onto *both* ubuntu and the external HD...to avoid the risk of everything going wrong.

Do you think I'll have to repeat this every boot or should it be ok now?

Also is this likely to make windows boot again?

---

### Post by michy99 on 2010-01-21
Did you try```
sudo mount -t ntfs-3g /dev/sda1 /media/windows
```
sorry, I see your reply.

---

### Post by michy99 on 2010-01-21
Well it doesn't solve the problem, but at least you can access the files.

---

### Post by sailthesea on 2010-01-21
A Live session will let you mount all partitions and extends and maybe get you to the root of problem
 More importantly you should be able to get to the files you desperately need
 It looks like its all there just a bit messed up:)
 Ah You got them 
 Good

---

### Post by DiegoDeEscocia on 2010-01-21
Ok I still have a problem....

That worked. I can view files and folders, I navigated to the folder where my essay was and it's empty....

A few folders next to it are similarly affected...Others are working without problems....I don't know much about these things but does it look to anyone else like there's a problem with the disk that affects the area I need to access?

Anything I  can run to repair it?

---

### Post by adam814 on 2010-01-21
You could try ntfsundelete (I think it's in the ntfsprogs package).  I haven't used it myself, but if the file was simply deleted that *might* get it back for you.

Other than that there are probably some general-purpose file-carving programs in the repos that might work for you.

---

### Post by sailthesea on 2010-01-21
..

---

### Post by DiegoDeEscocia on 2010-01-21
cheers guys, all of  your help is greatly appreciated, im installing ntfsprogs right now.


Will give it a shot!

---

### Post by DiegoDeEscocia on 2010-01-21
apparently need to unmount it before I can use undelete and it's failing because 1. I'm not root and 2. my drive isn't in fstab....? so it says....used the gui so the root part isnt surprising.......i'll sudo umount it. Just thought the fstab point might be useful to people here?

---

### Post by DiegoDeEscocia on 2010-01-21
only 2 recoverable files......

11001    FR..   100%  2010-01-12        80  <none>
23214    FR..   100%  2010-01-12        80  <none>


both from Jan 12th with no name..........

---

### Post by DiegoDeEscocia on 2010-01-22
Managed to track down a really old copy of the file which I'm going to submit. Not as good as the latest version but it'll do!

Thanks for your help all, anyone got any idea how to rectify the mystery of the missing windows installation once and for all?

Would be nice to recover my duel boot as there are a few things which I, lamentably, do need windows for!

Thanks again all!

---

### Post by synapsys on 2010-01-22
Have you tried going into the windows recovery console and running
```
fixboot
```and```
fixmbr
```

---

### Post by adam814 on 2010-01-22
Run this boot info script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post the results.

---

### Post by DiegoDeEscocia on 2010-01-26
Couldn't find my windows installation CD when I initially posted - fixmbr was one of the first things I wanted to try on it too.......


Ran the boot info script. The output follows:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: tipo de sistema de ficheros '' desconocido

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 60.0 GB, 60011642880 bytes
255 cabezas, 63 sectores/pista, 7296 cilindros, 117210240 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x00035ee7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    72,549,539    72,549,477   7 HPFS/NTFS
/dev/sda3          72,549,540   117,210,239    44,660,700   5 Extended
/dev/sda5         112,872,753   117,210,239     4,337,487  82 Linux swap / Solaris
/dev/sda6          72,549,666   112,872,689    40,323,024  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda5                                               swap                                     
/dev/sda6        a731b39c-801e-4752-8228-e7361977fc75   ext4                                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

/dev/sda6        /                ext4       (rw,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set a731b39c-801e-4752-8228-e7361977fc75
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a731b39c-801e-4752-8228-e7361977fc75 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=a731b39c-801e-4752-8228-e7361977fc75 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  37.1GB: boot/grub/core.img
  37.1GB: boot/grub/grub.cfg
  37.1GB: boot/initrd.img-2.6.31-14-generic
  37.1GB: boot/initrd.img-2.6.31-15-generic
  37.1GB: boot/initrd.img-2.6.31-16-generic
  37.1GB: boot/initrd.img-2.6.31-17-generic
  37.1GB: boot/vmlinuz-2.6.31-14-generic
  37.1GB: boot/vmlinuz-2.6.31-15-generic
  37.1GB: boot/vmlinuz-2.6.31-16-generic
  37.1GB: boot/vmlinuz-2.6.31-17-generic
  37.1GB: initrd.img
  37.1GB: initrd.img.old
  37.1GB: vmlinuz
  37.1GB: vmlinuz.old
```

Thanks guys and appologies for hte late response! I was dealling with essays and exams!

---

### Post by DiegoDeEscocia on 2010-01-26
I should say that I unmounted the windows drive again after having succeeded in seeing those files which hadn't dissapeared so it wasn't mounted at time of running the script (something else I tried required it be unmounted. Think it was the ntfsundelete function mentioned earlier!

the error

```

Mounting failed:
mount: tipo de sistema de ficheros '' desconocido
```

I believe the error means:

```
Mount Failed:
mount: Unknown filesystem
```

---

### Post by meierfra. on 2010-01-26
Running 

```
fixboot C: 
chkdsk /f C:
```


from your Windows XP CD, should fix your Windows partition. (Don't run "fixmbr". There is nothing wrong with your mbr and it would  overwrite Grub)  Then you will have to run 

```
sudo update-grub

```

in Ubuntu to add "XP" to the Grub menu. You will also have to add "Windows XP" to your fstab:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by DiegoDeEscocia on 2010-01-28
Thanks for the clear detailed answer! Sounds like you understand the problem - which is a massive relief!....

Shame my Windows XP CD is at my parents place.

Would it be possible to use a windows 7 CD to repair XP? As I have a friend with a copy of that handy....Else I'll need to wait until the next time I'm at my non-term time home.

*Will start to ask all of his friends for an XP CD he can borrow to fix his installation*

---

### Post by meierfra. on 2010-01-28
Yes, you should be able to use the Windows 7 CD:

Boot from the Windows 7 CD:

At the first screen select your favourite language.
Since you don't have Window 7 installed, the CD might not  let you go the command line directly. So we'll take to back road:
At the second screen choose "Install Now".
At the  license agreement  screen press "SHIFT+F10". 
This should open the command line.
Type 

```
diskpart
list volume
``` 
and take note of the drive letters for your XP partition and the CDrom drive. In the following I  assume that the XP partition is on "C:"and the CDrom is on "E:". But you have to replace those letters by the actual drive letters.

Type 

```
exit
E:\Boot\bootsect.exe /n52 C:
chkdsk /f C:
```

Then follow the instructions from my previous post to run update-grub and edit fstab.

---

