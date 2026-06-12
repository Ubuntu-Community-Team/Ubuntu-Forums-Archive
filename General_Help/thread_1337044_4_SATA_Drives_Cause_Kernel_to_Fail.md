---
title: "4 SATA Drives Cause Kernel to Fail"
date: 2009-11-25
forum: General Help
---

### Post by jamesisin on 2009-11-25
See this thread for the solution:

[http://ubuntuforums.org/showthread.php?t=1340530](http://ubuntuforums.org/showthread.php?t=1340530)






The problem is in the relationship between my /dev information and the boot loader.  See my most recent post (20091127 18:06).







I have a Dell box with this PCI 4 port SATA card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816102065](http://www.newegg.com/Product/Product.aspx?Item=N82E16816102065)

If I have two drive attached I can boot into Ubuntu 9.10 without issues.  However, if I attach all four drives I run into this little problem (image removed, see text in post below).

It doesn't seem to matter which two.  Two is fine; four is not; I didn't test three.

A little help?

---

### Post by listener on 2009-11-25
A possibility is that a 'false' raid array is being detected when all drives are connected.  Sorry I didn't check your link, but this is only a possibility.  You need to tell the thread what type of error you see if any, during boot.  

good luck

---

### Post by jamesisin on 2009-11-25
There is no error.  I will type out what is in the screen shot above:



GRUB loading.
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
mount: mounting /dev/sdc1 on /root failed: No such device
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _





(The underscore is the cursor.)

---

### Post by jamesisin on 2009-11-25
I could also say that boot goes fine up to a point, namely the little white Ubuntu symbol shows up (with a blue dashish line across the screen which isn't supposed to be there) and then the screen goes blank.  Touch a key reveals the above text (which was hidden behind the blank screen).

Oh, and three drives yields the same problem

---

### Post by jamesisin on 2009-11-27
Ok, I'm inching along.  If I boot with all four SATA drives attached my IDE (my OS) drive gets bumped from sdc (and sdc1, sdc2, and sdc5) to sde (and 1, 2, and 5).

What is the best route for correcting this?  Changing the bootloader to use sde?  Running a repair from the installation media?  Something else?

---

### Post by shaggy999 on 2009-11-28
What is probably happening is when you attach the extra drives your bootable drive gets bumped from sdc->sdd or similiar. If your grub and fstab are pointing to '/dev/sdx'-style devices then this causes a problem. You probably want to change the entries so that they instead point to the UUIDs of the drive.

I'm not inside ubuntu right now so I'm typing this from memory, but I believe the program 'tune2fs' has a parameter to read the UUID off of a drive. Then in fstab instead of the /dev/sdx reference you put UUID=XXXX-XXXXXX-XXXXX-XXXXXX to refer to the device. This way the boot process doesn't get confused and point to the wrong drive.

---

### Post by jamesisin on 2009-11-28
Shaggy999 - That sounds exactly like what I want.  If anyone can provide more detailed steps to help me get there, I'd be much obliged.

---

### Post by shaggy999 on 2009-11-28
So I'm in ubuntu now. If your drives are ext2/3/4 then you can use 'tune2fs' to query the UUID like this:

```
sudo tune2fs -l /dev/sda2 | grep UUID
```

In this case /dev/sda1 is my Vista partition and /dev/sda2 is my boot partition.

The output of that command looks like this:

```
Filesystem UUID:          5a5caea9-63a5-4266-8d41-8103f794b707
```

Now, in /etc/fstab I have an entry for /boot that looks like this:

```
/dev/sda2 /boot ext2 defaults 0 2
```

This can be changed to:
```

UUID=5a5caea9-63a5-4266-8d41-8103f794b707 /boot ext2 defaults 0 2
```

This change ensures that linux knows exactly which drives to mount without worrying about which ports they're plugged in on. Grub may also need something similiar done, but the new grub2 in karmic works completely differently from grub and I have no idea how to fiddle with it. But chances are if your system at least starts to boot the kernel currently then grub may not need any messing with.

One other thing, if you are currently using lvm/raid/luks then the /dev/sdX is probably NOT what you want to run tune2fs on. In my situation I have a luks+lvm2 setup and my "partitions" are located under /dev/mapper. So for my root partition, for example, I run:

```
sudo tune2fs -l /dev/mapper/ubuntu-root | grep UUID
```

---

### Post by jamesisin on 2009-11-28
My OS partition is a lone partition on a lone IDE drive.  It would seem that following this method will take care of the matter.

If you have any caveats, now is the time.  I'll likely test this change in the morning.

---

### Post by QLee on 2009-11-28
Mounting by UUID is a correct solution, you will probably need to change GRUB configuration so that it tries to boot from the correct device, which doesn't seem to be happening when you have all connected and the system reorders the device nodes.

Another solution would be to mount by label, if you have labelled your partitions.

Both the UUID and LABEL method of mounting work because the UUID should be "unique" (2nd U) and label works if you only name one partition on your system with that specific label.

Edit:If you had installed 9.10 with all the drives attached, installing GRUB would very likely have taken care of things for you. Did you do an upgrade from a previous version and leave legacy grub as your bootloader, GRUB 2 uses UUIDs when it is installed during Ubuntu installation and what you have shown seems to indicate that device nodes are being used?

Is that "lone" device you mention actually separate from the 4 you mention, It seems your GRUB is trying to boot from whatever was the third device enumerated at installation time (sdc).

---

### Post by jamesisin on 2009-11-28
This was a fresh 9.10 installation on essentially empty hardware (a scrub and build).  The IDE drive was the only drive present during installation.  Two of the SATA drives were attached shortly after the build.  The final two drive I attached even later.  I don't understand why the IDE drive received c and not a to begin with, nor (if what you say is correct about Grub2) why this machine is not already using UUID's (unless Grub2 is, but fstab is not).  Is there a way I can peek at Grub2 before I perform surgery on fstab?

---

### Post by shaggy999 on 2009-11-28
The problem is that IDE drives are generally enumerated AFTER SATA drives during the boot process. So when you add SATA drives post-installation it pushes the IDE drive farther back.

If you have a bootable system then changing fstab from /dev/sdX to UUID should not affect anything. You don't need to worry about grub getting confused. So start with that BEFORE you add SATA drives.

The problem with grub will occur when you try to add the SATA drives. So go ahead and do the fstab change but don't assume that fixes the problem quite yet. The problem is that fstab tells LINUX where the drives are, grub doesn't use fstab. That's why you have to do it in both places to get the results you want, but it's safe to do them seperately before you add the drives, but both have to be done in order to add the drives.

---

### Post by jamesisin on 2009-11-28
And how do I go about changing Grub?

---

### Post by shaggy999 on 2009-11-28
That's the part I'm unsure about as ubuntu now uses grub2 which is completely different from the original grub.

---

### Post by sdowney717 on 2009-11-28
grub2 guide
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

here is my grub2 grub.cfg file located in /boot/grub/grub.cfg
I notice my grub2 is using uuid

> #
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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
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
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-15-generic-pae root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-14-generic-pae root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.28-15-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.28-14-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 4923760a-6e34-4678-b0ab-d06b151a2998
	linux	/boot/vmlinuz-2.6.28-11-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro single 
	initrd	/boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 26e82022e81feeb5
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by jamesisin on 2009-11-28
Perhaps I am using Grub (and not Grub2).  How can I determine that?

Mine is using a /dev path:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-15-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-14-generic root=/dev/sdc1 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###
```

Can I just change those references to use the UUID then?

If that is the case I would need to change each of the four "root=/dev/sdc1 ro" to something different?  Or is the "ro" not part of it?

(Running tune2fs gives "Filesystem UUID:          b8c9f44c-af18-4bfc-919a-5941628aa25b".)

---

### Post by jamesisin on 2009-11-28
This is from my fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b8c9f44c-af18-4bfc-919a-5941628aa25b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5e0c996c-676c-45a5-87ff-3f78eb157646 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I suppose I don't need to change anything here then?

I'll have to keep an eye on the CD drive after I attach the second pair of SATA's--to see if it goes AWOL.

---

### Post by shaggy999 on 2009-11-28
It looks like your fstab is fine.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
```

Taken straight from that file. Don't edit that file directly. Looks like you need to make your changes elsewhere.

---

### Post by jamesisin on 2009-11-28
Yeah, I saw that.

Anybody able to fill in the details of how to make these changes to Grub?

---

### Post by redmk2 on 2009-11-28
See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("https://help.ubuntu.com/community/Grub2").

As a matter of fact if you google the terms *Ubuntu grub2* you get [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://www.google.com/search?q=ubuntu+grub2&btnG=Go!").

---

### Post by jamesisin on 2009-11-28
redmk2 - The change we are talking about in this thread is not explicitly outlined in the page you suggested.  And I know how Google works.

---

### Post by shaggy999 on 2009-11-28
So I'm looking through the files and it looks like you want to open '/etc/default/grub' and make sure that the following line does NOT exist:

```
GRUB_DISABLE_LINUX_UUID=true
```

If it exists then comment it out with a #. Then run the following command:

```
sudo update-grub
```

After you do that check /boot/grub/grub.cfg and it should be using UUIDs now.

---

### Post by jamesisin on 2009-11-28
Unfortunately, it is already commented out.

---

