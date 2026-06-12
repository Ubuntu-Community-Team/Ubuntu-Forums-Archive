---
title: "How to downgrade Grub2 to Grub legacy with offline live cd"
date: 2010-12-04
forum: General Help
---

### Post by roshgorg on 2010-12-04
I have a Dell Studio 1558 laptop. I installed Ubuntu 10.10 a few days before, and it works like a charm. Also, since my laptop is used by my father too, I have a Windows 7 installation in my laptop. Once, when I boot to Windows, and then restarted, Grub fails. It says, no module found. So, I once again installed Ubuntu 10.10. When I searched the forums, it says, downgrade the Grub2 to Grub legacy, and there will not be any problem working with Windows....

With the command for removing Grub2 and insatlling Grub legacy with the command "sudo apt-get install grub" , I can't finish my work, because, I don't have wired internet access. I only have a mobile phone to connect to internet using mobile broadband. Also, mobile broadband is disabled in Ubuntu 10.10 . So, the possibility of downgrading via internet is very low.

I have a live cd of Ubuntu 9.04, which has Grub legacy. Is there a way to install Grub legacy using the Ubuntu 9.04 live CD. Please help.

Currently my state is :- I have a new installation of Ubuntu 10.10 . I haven't booted to Windows. Please provide me help to downgrade to Grub legacy using ubuntu 9.04 live cd.

Thanks in advance.....

---

### Post by wilee-nilee on 2010-12-04
Before we go to grub legacy lets have a look at the system.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

To be honest grub2 is a much better setup you may just have some problems that can be fixed.;)

---

### Post by roshgorg on 2010-12-04
> **wilee-nilee said:**
> Before we go to grub legacy lets have a look at the system.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

To be honest grub2 is a much better setup you may just have some problems that can be fixed.;)

Do, i need to boot from ubuntu 10.10 live cd and then run the script?

---

### Post by sikander3786 on 2010-12-04
> **roshgorg said:**
> Do, i need to boot from ubuntu 10.10 live cd and then run the script?
Yes. Either boot a working Linux install on the HDD or from a Linux Live CD.

---

### Post by roshgorg on 2010-12-04
> **sikander3786 said:**
> Yes. Either boot a working Linux install on the HDD or from a Linux Live CD.

Currently, i am accessing internet through windows, because, my mobile broadband is disabled in Ubuntu 10.10. 

SO, If i go to Ubuntu 10.10 and run the script and save the script in a text file. I will need to logon to window in order to paste the results here in this forum, and after that I will not be able to log into either Ubuntu or Windows, because it will say-"no modules found. try again".

What should i do then ?

---

### Post by sikander3786 on 2010-12-04
Sorry I didn't concentrate at your initial post at first :-) Now I know ;-)

I can't figure out any workaround for you issue. If you have access to some other PC with internet or at least Windows so you can access mobile broadband from that?

Or if you could repair the Windows startup from Windows recovery/startup disk after you run the script and if unable to boot Windows then....

What did you use to do earlier when you go that "no module found" error?

---

### Post by roshgorg on 2010-12-05
> **sikander3786 said:**
> Sorry I didn't concentrate at your initial post at first :-) Now I know ;-)

I can't figure out any workaround for you issue. If you have access to some other PC with internet or at least Windows so you can access mobile broadband from that?

Or if you could repair the Windows startup from Windows recovery/startup disk after you run the script and if unable to boot Windows then....

What did you use to do earlier when you go that "no module found" error?


what i did when such error came was, i recovered Windows bootloader with help of command prompt in the recovery section of windows 7 installation disk.....
When i do so, Grub will be lost...
Does that create any problem

---

### Post by wilee-nilee on 2010-12-05
So here is the problem probably.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

So reload the MS bootloader with the disc with this command from the repair, recovery command line.
```
bootrec.exe /fixmbr
```

Look for the dell data safe in add remove we can reload grub if this is the problem.

---

### Post by sikander3786 on 2010-12-05
> **roshgorg said:**
> what i did when such error came was, i recovered Windows bootloader with help of command prompt in the recovery section of windows 7 installation disk.....
When i do so, Grub will be lost...
Does that create any problem
Unless **wilee-nilee** can suggest something better, I would suggest to boot the Live CD, run the bootinfoscript, recover Windows bootloader and post the output if you've got no other choice.

We can give you links to install Grub2 or downgrade to Grub legacy but it would be better if you let us see the boot script output ;-)

Then we might be able to give you the exact solution.

---

### Post by wilee-nilee on 2010-12-05
I looked up that computer model and it mentions the dell data safe on several web sites as being installed.

We just have to get the actual partitions correct for the reinstall of grub2 and you should be set.

---

### Post by roshgorg on 2010-12-05
Hello to Sikander and Wilee-nilee,

Currently, I reinstalled ubuntu 10.10, and run the above said script named boot_info_script. The results are 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       273,104       273,042  de Dell Utility
/dev/sda2    *        274,432    20,996,095    20,721,664   7 HPFS/NTFS
/dev/sda3          20,996,096   241,190,911   220,194,816   7 HPFS/NTFS
/dev/sda4         241,192,958   976,771,071   735,578,114   f W95 Ext d (LBA)
/dev/sda5         241,192,960   596,398,079   355,205,120   7 HPFS/NTFS
/dev/sda6         596,400,128   951,605,247   355,205,120   7 HPFS/NTFS
/dev/sda7         951,607,296   975,794,175    24,186,880  83 Linux
/dev/sda8         975,796,224   976,771,071       974,848  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        826A-B2C3                              vfat                                     
/dev/sda2        DC606D7E606D606E                       ntfs       RECOVERY                      
/dev/sda3        66B070A3B0707B7F                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2A0284270283F5DB                       ntfs       DATA                          
/dev/sda6        F4C2276FC2273570                       ntfs       OTHERS                        
/dev/sda7        6f47280c-d87d-41ee-8f95-c755840e4a24   ext4                                     
/dev/sda8        f0cf6490-9b38-46b8-873d-ebff75621345   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 6f47280c-d87d-41ee-8f95-c755840e4a24
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 6f47280c-d87d-41ee-8f95-c755840e4a24
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6f47280c-d87d-41ee-8f95-c755840e4a24
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6f47280c-d87d-41ee-8f95-c755840e4a24 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6f47280c-d87d-41ee-8f95-c755840e4a24
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6f47280c-d87d-41ee-8f95-c755840e4a24 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6f47280c-d87d-41ee-8f95-c755840e4a24
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6f47280c-d87d-41ee-8f95-c755840e4a24
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set dc606d7e606d606e
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=6f47280c-d87d-41ee-8f95-c755840e4a24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=f0cf6490-9b38-46b8-873d-ebff75621345 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 496.0GB: boot/grub/core.img
 496.0GB: boot/grub/grub.cfg
 488.3GB: boot/initrd.img-2.6.35-22-generic
 496.0GB: boot/vmlinuz-2.6.35-22-generic
 488.3GB: initrd.img
 496.0GB: vmlinuz

```



Now I am in Windows 7....I mean, i connected to internet via WIndows 7.. Next time I reboot, there won't be Grub.....At that tyme, I will need to fix my windows mbr, and then remove Dell Datasafe local from my Add/Remove programs. Right?

Then I need to boot to Ubuntu live cd and then try "http://blog.mattrudge.net/2010/05/06/dual-boot-in-ubuntu-10-04/ " .Right.?


note:- after installing Ubuntu, I once logged in to it. After the bootloader og Grub, a message was displayed at the top of the screen...I could just read "Gui disabled".....It was just a flash message and the boot screencame up...Is the new Grub having any graphics..does that mean graphics is disabled in myy grub2?

---

### Post by wilee-nilee on 2010-12-05
So what we have here is failure to communicate, why do I here banjos in the background.;)

I have very little patience in this sort of situation where the basic instructions aren't followed and you do your own voodoo in the back ground I give up sorry.;)

---

### Post by roshgorg on 2010-12-05
> **wilee-nilee said:**
> So what we have here is failure to communicate, why do I here banjos in the background.;)

I have very little patience in this sort of situation where the basic instructions aren't followed and you do your own voodoo in the back ground I give up sorry.;)


I am sorry....I reinstalled Ubuntu because, Windows installation disk wasn't loading, so that i can repair..
since it wasn't been loading i reinstalled ubuntu...sorry.....

please dont leave me in such a situation....

---

### Post by sikander3786 on 2010-12-05
A reinstall was not needed as **wilee-nilee** suggested above. (I would request wilee-nilee to help you :P )

And obviously due to a reinstall of Ubuntu/Grub, I don't see any boot files for Windows but there is an entry for Windows 7 in 30_os-prober :confused:

There have been cases where Windows loaders overwrite Grub. And in those cases, instead of making Grub persistent, if you can live with EasyBCD, I would suggest a Windows boot loader capable of booting Ubuntu.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

All you need to do is to restore Windows boot loader > Boot Windows 7 and follow the instructions on the link mentioned above.

Might be some-one else comes up with some better suggestion regarding the use of Grub, unfortunately, I can't :-)

Good Luck!

---

### Post by roshgorg on 2010-12-05
> **sikander3786 said:**
> A reinstall was not needed as **wilee-nilee** suggested above. (I would request wilee-nilee to help you :P )

And obviously due to a reinstall of Ubuntu/Grub, I don't see any boot files for Windows but there is an entry for Windows 7 in 30_os-prober :confused:

There have been cases where Windows loaders overwrite Grub. And in those cases, instead of making Grub persistent, if you can live with EasyBCD, I would suggest a Windows boot loader capable of booting Ubuntu.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

All you need to do is to restore Windows boot loader > Boot Windows 7 and follow the instructions on the link mentioned above.

Might be some-one else comes up with some better suggestion regarding the use of Grub, unfortunately, I can't :-)

Good Luck!

thanks... why did it say gui disabled?

Do i need to do what wilee-nilee said? like restoring the windows mbr, and then uninstalling dell datasafe, and then do correcting grub....

please reply

---

### Post by sikander3786 on 2010-12-05
> **roshgorg said:**
> thanks... why did it say gui disabled?

Do i need to do what wilee-nilee said? like restoring the windows mbr, and then uninstalling dell datasafe, and then do correcting grub....

please reply
Might be the gui problem goes away after you install your graphics driver.

And what **wilee-nilee** said, sounds like the best method to get Grub going. I don't feel comfortable with recovery and datasafe partitions as I have never used them and obviously can't advise on that.

Hang in there and **wilee-nilee** might be back soon ;-)

---

### Post by wilee-nilee on 2010-12-05
So this is kind of convoluted as the script makes it look as if W7 shouldn't even boot, but the script is not always accurate especially if there are problems in windows.

Here is a recovery disc link I will post the command again to reload the MS boot loader if you can't get into windows.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Then reboot to W7 and look in add remove or whatever it is called to remove programs for the dell data safe.

Notice the instructions to get to the command line by booting a install or recovery disc I have given the link for. There is also the W7 forums link to orientate you if needed.

If you have dell data safe you will not have a working dual boot the dell program overwrites the boot.

The mattrudge link is correct for reloading grub, just make sure you use the same cd=the Ubuntu installed to put grub back in the mbr.

Sorry for the ruckus I have had some things happen in my life which is making me even more evil then my usual self I am sorry.;)

If any of this doesn't make sense just post back with any questions in the end we want you fixed and happy.

**Edit:**really the script shows some anomalies that just make me wonder whats up, those that can read the script will see what I mean sda5 starting at 2048?, missing windows boot stanzas, it is hard to say here really.

The second load of Ubuntu might be part of this I just don't know, to be honest with the script looking the way it is I would personally let a more experienced forum member help. But it took so long to get the actual script that I was into trying to work around the lack of the script.

If you had posted that script originally I would have said wait for a more knowledgeable user. That is why the script is so important so we don't give you improper instructions.

---

### Post by roshgorg on 2010-12-05
> **wilee-nilee said:**
> So this is kind of convoluted as the script makes it look as if W7 shouldn't even boot, but the script is not always accurate especially if there are problems in windows.

Here is a recovery disc link I will post the command again to reload the MS boot loader if you can't get into windows.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Then reboot to W7 and look in add remove or whatever it is called to remove programs for the dell data safe.

Notice the instructions to get to the command line by booting a install or recovery disc I have given the link for. There is also the W7 forums link to orientate you if needed.

If you have dell data safe you will not have a working dual boot the dell program overwrites the boot.

The mattrudge link is correct for reloading grub, just make sure you use the same cd=the Ubuntu installed to put grub back in the mbr.

Sorry for the ruckus I have had some things happen in my life which is making me even more evil then my usual self I am sorry.;)

If any of this doesn't make sense just post back with any questions in the end we want you fixed and happy.

**Edit:**really the script shows some anomalies that just make me wonder whats up, those that can read the script will see what I mean sda5 starting at 2048?, missing windows boot stanzas, it is hard to say here really.

The second load of Ubuntu might be part of this I just don't know, to be honest with the script looking the way it is I would personally let a more experienced forum member help. But it took so long to get the actual script that I was into trying to work around the lack of the script.

If you had posted that script originally I would have said wait for a more knowledgeable user. That is why the script is so important so we don't give you improper instructions.


hello wilee-nilee...i have a doubt.

after i recover windows mbr with the above code, and remove de;; datasafe, what should i do?

---

### Post by roshgorg on 2010-12-05
> **wilee-nilee said:**
> So this is kind of convoluted as the script makes it look as if W7 shouldn't even boot, but the script is not always accurate especially if there are problems in windows.

Here is a recovery disc link I will post the command again to reload the MS boot loader if you can't get into windows.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Then reboot to W7 and look in add remove or whatever it is called to remove programs for the dell data safe.

Notice the instructions to get to the command line by booting a install or recovery disc I have given the link for. There is also the W7 forums link to orientate you if needed.

If you have dell data safe you will not have a working dual boot the dell program overwrites the boot.

The mattrudge link is correct for reloading grub, just make sure you use the same cd=the Ubuntu installed to put grub back in the mbr.

Sorry for the ruckus I have had some things happen in my life which is making me even more evil then my usual self I am sorry.;)

If any of this doesn't make sense just post back with any questions in the end we want you fixed and happy.

**Edit:**really the script shows some anomalies that just make me wonder whats up, those that can read the script will see what I mean sda5 starting at 2048?, missing windows boot stanzas, it is hard to say here really.

The second load of Ubuntu might be part of this I just don't know, to be honest with the script looking the way it is I would personally let a more experienced forum member help. But it took so long to get the actual script that I was into trying to work around the lack of the script.

If you had posted that script originally I would have said wait for a more knowledgeable user. That is why the script is so important so we don't give you improper instructions.


I have removed Dell Data Safe....
What to do next...Do i need to do this [http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/](http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/) now?

---

### Post by sikander3786 on 2010-12-05
> **roshgorg said:**
> I have removed Dell Data Safe....
What to do next...Do i need to do this [http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/](http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/) now?
wilee-nilee seems away at the moment so I must jump back ;-)

Are you able to boot Windows succesfully now?

---

### Post by roshgorg on 2010-12-05
> **wilee-nilee said:**
> So this is kind of convoluted as the script makes it look as if W7 shouldn't even boot, but the script is not always accurate especially if there are problems in windows.

Here is a recovery disc link I will post the command again to reload the MS boot loader if you can't get into windows.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Then reboot to W7 and look in add remove or whatever it is called to remove programs for the dell data safe.

Notice the instructions to get to the command line by booting a install or recovery disc I have given the link for. There is also the W7 forums link to orientate you if needed.

If you have dell data safe you will not have a working dual boot the dell program overwrites the boot.

The mattrudge link is correct for reloading grub, just make sure you use the same cd=the Ubuntu installed to put grub back in the mbr.

Sorry for the ruckus I have had some things happen in my life which is making me even more evil then my usual self I am sorry.;)

If any of this doesn't make sense just post back with any questions in the end we want you fixed and happy.

**Edit:**really the script shows some anomalies that just make me wonder whats up, those that can read the script will see what I mean sda5 starting at 2048?, missing windows boot stanzas, it is hard to say here really.

The second load of Ubuntu might be part of this I just don't know, to be honest with the script looking the way it is I would personally let a more experienced forum member help. But it took so long to get the actual script that I was into trying to work around the lack of the script.

If you had posted that script originally I would have said wait for a more knowledgeable user. That is why the script is so important so we don't give you improper instructions.


I have removed Dell Data Safe....
What to do next...Do i need to do this [http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/](http://mattrudge.wordpress.com/2010/05/06/dual-boot-in-ubuntu-10-04/) now?

---

### Post by roshgorg on 2010-12-05
> **sikander3786 said:**
> wilee-nilee seems away at the moment so I must jump back ;-)

Are you able to boot Windows succesfully now?

yes, now i can boot to windows only... i am going to do what Vilee-nilee said....

---

### Post by sikander3786 on 2010-12-05
> **roshgorg said:**
> yes, now i can boot to windows only... i am going to do what Vilee-nilee said....
Once able to boot Windows successfully, you need to do these commands from Ubuntu Live CD.

```
sudo mount /dev/sda7 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second one it is just sda without an integer and not sda7.

Reboot and see if it dual boots successfully.

Good Luck!

---

### Post by roshgorg on 2010-12-05
> **sikander3786 said:**
> Once able to boot Windows successfully, you need to do these commands from Ubuntu Live CD.

```
sudo mount /dev/sda7 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```Note, for the second one it is just sda without an integer and not sda7.

Reboot and see if it dual boots successfully.

Good Luck!


but the 3rd code " sudo unmount /mnt" does not work..it says command unmount not found....

but it is working properly now...

thanks to all of your help...

I have another problem with Ubuntu 10.10 ...The "mobile broadband" is disabled...When i click to enable it, nothing happens....how to make the mobile broadband work?

also, how to enable gui of Grub2

---

### Post by sikander3786 on 2010-12-05
> " sudo unmount /mnt"

Where did you get that from? That was not in my post.

> also, how to enable gui of Grub2

What do you mean by GUI? Don't you see the Grub menu at boot?

Or if you want to play with some Grub options, Startup Manager is the best choice.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Regarding mobile broadband, that needs a new thread in appropriate sub-forum ;-)

---

### Post by roshgorg on 2010-12-05
> **sikander3786 said:**
> Where did you get that from? That was not in my post.



What do you mean by GUI? Don't you see the Grub menu at boot?

Or if you want to play with some Grub options, Startup Manager is the best choice.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Regarding mobile broadband, that needs a new thread in appropriate sub-forum ;-)


The Grub menu is displayed properly, but when i select Ubuntu, a flash message is shown saying gui disabled.....why is that.....

GUI is graphical user interface

---

### Post by roshgorg on 2010-12-05
Thanks you very much Sikander3786and Wilee-nilee... you both were very supporting....thanks

---

### Post by wilee-nilee on 2010-12-05
If your able to boot to Windows or Ubuntu, I think your okay. With open source and Ubuntu things change and you will see what look like cryptic messages on startup after choosing Ubuntu. The whole area from the bootloader=grub to the desktop is going through a lot of upgrades being done by different teams, so if it boots normally I never worry about a little text on the screen I don't even understand.

I had to get some sleep glad to see things seem to be fixed. Thanks sikander3786.;)

---

### Post by sikander3786 on 2010-12-05
> I had to get some sleep glad to see things seem to be fixed. Thanks sikander3786.

Welcome boss. Most Welcome :-)
[B]
To the OP:[/B] You can now mark this thread Solved (on behalf of all the contributors) using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

