---
title: "grub 1.97 beta problem after upgrade to 10.04"
date: 2010-04-29
forum: General Help
---

### Post by Dr-a on 2010-04-29
hi everyone ..

during the upgrade proses I had lots of errors !
anyway my problem happened when I chose keep my modified boot loader and I didn't install the new grub boot loader :(

now .. when I start my laptop I get into the command line $

I have tow HDD (ubuntu/ win7)


how can I fix it ?:confused:

---

### Post by Dr-a on 2010-04-30
please help me

---

### Post by carl4926 on 2010-04-30
Boot the Ubuntu CD to live desktop

* Open a terminal and type

```
sudo fdisk -l
```

    * Now, you need to remember which device listed is your Ubuntu distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

```
sudo mount /dev/sda1 /mnt
```

    * Now mount the rest of your devices

```
sudo mount --bind /dev /mnt/dev

```
    * Now chroot into your system

```
sudo chroot /mnt
```

    *

      When that is done you need to run update-grub to create the configuration file.

```
update-grub

```
    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

```
grub-install /dev/sda

```
And your done

---

### Post by Dr-a on 2010-04-30
thanks .. I got my old boot screen but the problem still the same !
when I boot up it takes me to the login user and password "by command" 
```

user-login: 
password :
```when I login in the command line I get 

```
dr-a laptop $ 
```
also when I did this command 

update-grub

some of the results were unable to found and some were found



also this command has no results at all "unable to find somthing

grub-install /dev/sda



Do you think my problem could be due to the kernel ??:confused:
because my laptop is 32 bit and only support 3GB Ram , somehow I could change it to 4GB Ram I think by changing the kernel :confused:


my boot screen has ...

```

ubuntu 2.6.32-21
ubuntu 2.6.31-21
ubuntu 2.6.31-20
windows7 loader 

```

Can you help me PLEASE ?:(

---

### Post by carl4926 on 2010-04-30
Actually your grub looks OK
The directions I gave you were to be run from a Live CD.

But forget that and boot to the command line like you did before. When you have logged it and are at
[I]dr-a laptop $
[/I]
type:** startx**

see if it boots to a UI

If it doesn't, please try updating. Like this

```
sudo aptitude update
```
then
```
sudo aptitude full-upgrade
```

then reboot.

P.S: Can you boot in to windows?

---

### Post by Dr-a on 2010-04-30
thanks I'll try this now

and yes I can boot into windows

---

### Post by Dr-a on 2010-04-30
I did startx and it worked but in Low graphical mode :confused:
problem in Gnome and the power manager couldn't be installed !

I typed 

sudo aptitude update
and 

sudo aptitude full-upgrade

and I got 

couldn't open locked file /var/lib/apt/lists/lock-open (2:no such file or directory 
E: couldn't open file are you root ?

what can I do ?:confused:
and thanks in previous

---

### Post by carl4926 on 2010-04-30
> couldn't open locked file /var/lib/apt/lists/lock-open (2:no such file  or directory 
E: couldn't open file are you root ?

This may be because you had another package manager running/
Reboot and try again.
If you do it before you get to the desktop - ie; at the CLI, that should do it.

I suspect you need to update your graphics driver. Depends what you have?

---

### Post by Dr-a on 2010-04-30
I can't boot up normally I boot by using Startx only ""with low graphics and installation errors ""

the screen is black and there is no tool bar on the top !
my driver is 
			 				ATI radeon HD 3470 

I think the problem starts from not booting automatically :confused:
also the problems in gnome and power manager and the error :
                             > couldn't open locked file /var/lib/apt/lists/lock-open (2:no such  file  or directory 
E: couldn't open file are you root ? Is there any solution for my problems ?
should I Install the system again ?   :(

---

### Post by Dr-a on 2010-04-30
I need help please


main problems : 

		-I can't boot up normally I boot by using Startx only ""with low  graphics and installation errors ""

- the screen is black and there is no tool bar on the top !

- when I try some commands like gnome installation or update or upgrade,  I get 

[COLOR=Red]couldn't open locked file /var/lib/apt/lists/lock-open (2:no such  file   or directory 
E: couldn't open file are you root ? 			 		[/COLOR]

-Gnome couldn't be configured "installation error"

- power manager error

[COLOR=Red]the initial problem was grub problem . I restored my old boot but  I  still cant boot automatically I must type Startx[/COLOR]


Im totally screwed :(
anyone can help ?

---

### Post by dino99 on 2010-04-30
first we need to fix boot problem:

into a console, run:
- sudo grub-mkconfig && update-grub

now about graphic:
- sudo apt-get install radeontool xserver-xorg-video-radeon
then
- sudo rm -f /etc/X11/xorg.conf
- sudo dpkg-reconfigure jockey-gtk

reboot and let me know how it goes

note: better to copy/paste to not have mistakes

---

### Post by dino99 on 2010-04-30
a question about your config:

as it is a dist-upgrade, previously it was grub2 or grub1 (grub-legacy) ?

If you had grub1 installed, first goto synaptic and remove/purge every grub packages and reinstall grub-pc and grub-common (installation might be on your lucid partition (/dev/sda or so))

---

### Post by carl4926 on 2010-04-30
@dino99

I can see you know your way around, but our friend here does not.

So far He has failed to see that there is no need to startx to be actually logged in. He may not quite realize that the command line login is 'Console'. Because I already gave him instruction to run an update be he still pressed on to startx before hand.

@Dr-a
Apologies for speaking of you in 3rd person above, but @dino99 seem somewhat more qualified than myself. Please look carefully at what he posted. And if possible 'Don't Panic'!

Where you can, please explain carefully how you have upgraded. Is it possible you were using grub1 (legacy). A clue might be if your partitions are ext3 not ext4.

---

### Post by Dr-a on 2010-04-30
thank you all ...
the problem still unsolved

I have also a problem that the tool bar on the top is gone !

@dino99
Idont know what do you mean by:
 
> a question about your config:
sorry im a new ubuntu user

I did all of the commands and here are my results

sudo grub-mkconfig

I got


  >   set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=43704200-64cf-42ee-9f3c-e85e9c2dc699 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic-pae
}
Found linux image: /boot/vmlinuz-2.6.31-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-21-generic-pae
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=43704200-64cf-42ee-9f3c-e85e9c2dc699 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    echo    'Loading Linux 2.6.31-21-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-21-generic-pae root=UUID=43704200-64cf-42ee-9f3c-e85e9c2dc699 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic-pae
}
Found linux image: /boot/vmlinuz-2.6.31-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-20-generic-pae
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=43704200-64cf-42ee-9f3c-e85e9c2dc699 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    echo    'Loading Linux 2.6.31-20-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=43704200-64cf-42ee-9f3c-e85e9c2dc699 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 43704200-64cf-42ee-9f3c-e85e9c2dc699
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Windows 7 (loader) on /dev/sdb1
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a6e27c6de27c4419
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
done







update-grub> 
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-21-generic-pae
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.31-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-21-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-20-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done






sudo apt-get install radeontool xserver-xorg-video-radeon

> root@dr-a-laptop:/# sudo apt-get install radeontool xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
radeontool is already the newest version.
xserver-xorg-video-radeon is already the newest version.
The following packages were automatically installed and are no longer required:
  python-multiprocessing libfreebob0 xfprint4 libxine1-x wine-gecko
  libkadm5clnt-mit7 libsdl-gfx1.2-4 vcdimager comerr-dev
  xfce4-volumed libglew1.5 libxine1-misc-plugins libxcb-xv0
  libxmlrpc-c3 libass3 libxine1-bin libkrb5-dev python2.4
  libboost-thread1.38.0 libkadm5clnt6 libldap2-dev dvdauthor
  libgssrpc4 libtre4 sdparm libx264-67 r-cran-vr ocaml ruby
  libxine1-ffmpeg libcelt0 krb5-multidev xfce4-screenshooter-plugin
  libssl-dev libxcb-shape0 libboo2.0-cil libffado1 libiso9660-5
  fglrx-kernel-source python-sqlite libxine1-plugins libxml++2.6-2
  libkadm5srv-mit7 libfaad-dev ocaml-base libffmpegthumbnailer3
  libdb4.6 xsel libkdb5-4 libboost-filesystem1.38.0 libxcb-shm0
  mplayer-nogui libreadline5 libboost-system1.38.0 libidn11-dev
  libcurl4-openssl-dev libxine1-console libhildon-1-0
  libboost-python1.38.0 libfaad0 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
750 not fully installed or removed.
E: Lists directory /var/lib/apt/lists/partial is missing.






sudo rm -f /etc/X11/xorg.conf

> nothing happened 






sudo dpkg-reconfigure jockey-gtk

> root@dr-a-laptop:/# sudo dpkg-reconfigure jockey-gtk
/usr/sbin/dpkg-reconfigure: jockey-gtk is broken or not fully installed



@carl4926

I upgraded through the system update in administration

---

### Post by dino99 on 2010-04-30
seem you have made lot of tweaks  :confused:

maybe its faster to reinstall with a clean new lucid distro, dont you :rolleyes:

---

### Post by Dr-a on 2010-04-30
I thought Linux can be fixed what ever happened , unfortunately this  is not true I guess !

okay I think I'll reinstall it again 

thank you all

---

### Post by carl4926 on 2010-04-30
> **Dr-a said:**
> I thought Linux can be fixed what ever happened 

thank you all

I never did hear that.
I don't subscribe to such an idea either.

A re-install is a good idea IMO.

---

