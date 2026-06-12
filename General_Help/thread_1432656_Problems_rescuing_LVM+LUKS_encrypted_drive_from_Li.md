---
title: "Problems rescuing LVM+LUKS encrypted drive from LiveCD."
date: 2010-03-18
forum: General Help
---

### Post by Thaddeus Morgan on 2010-03-18
I munged my GRUB when I installed 9.10 from a LiveCD onto a USB hard drive.  After ejecting the LiveCD and disconnecting the hard drive, I can no longer boot my machine.  GRUB tells me something to the effect that the disc isn't found.  My guess is that installing onto an external USB drive modified my GRUB settings on my internal hard drive.  The problem is that my internal drive is encrypted via LVM+LUKS. My plan is to boot into the LiveCD, unlock my internal drive, mount my internal drive, chroot into my internal drive's Ubuntu 9.10 installation, fix GRUB, and live happily ever after.  Unfortunately, I'm stuck at decrypting my internal drive.  From everything I've gathered (e.g. [http://ubuntuforums.org/showthread.php?t=611165](http://ubuntuforums.org/showthread.php?t=611165)), the steps I need to do this are:

1) sudo su
2) aptitude install lvm2 cryptsetup
3) modprobe dm-crypt
4) cryptsetup luksOpen /dev/sda5 crypt1

The last step gives me this error, which doesn't seem to be explained in any of the threads I've seen on the subject:
Command failed: Can not access device

Which is strange, because "cryptsetup isLuks /dev/sda5" returns true and looking at fdisk -l reveals:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xDEADBEEF

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13       30401   244099642+   5  Extended
/dev/sda5              13       30401   244099611   83  Linux

Any suggestions?

Thanks,
TM

---

### Post by Thaddeus Morgan on 2010-03-18
As it turns out, booting from the USB drive instead of the Live CD solves the problem of not being able to unlock my encrypted internal drive.  Now I have a different problem.  Here's what I've done so far, all successfully:

[LIST=1]
[*]Boot from USB drive.
[*]sudo aptitude install lvm2 cryptsetup
[*]sudo modprobe dm-crypt
[*]sudo cryptsetup luksOpen /dev/sda5 crypt1
[*]sudo vgscan --mknodes
[*]sudo vgchange -ay
[*]sudo mkdir /media/crypt_root
[*]sudo mount /dev/vg1/lvroot /media/crypt_root
[*]sudo mount -o bind /proc /media/crypt_root/proc
[*]sudo mount -o bind /dev /media/crypt_root/dev
[*]sudo chroot /media/crypt_root /bin/bash
[*]update-grub
This command results in:
  Generating grub.cfg ...
  Cannot find list of partitions!
  done
[*]grub-install hd0
This command results in:
  grub-probe: error: no mapping exists for 'vg1-lvroot'
  Auto-detection of filesystem module failed.
  Please specify the module with the option `--modules' explicitly.
[/LIST]

The last two steps are where I'm stuck.  The /boot/grub/device.map on my internal drive is:

(hd0)   /dev/sda
(hd1)   /dev/sdb

Looking at /boot/grub/grub.cfg, I see that root is set to (hd1,1).  I would like it to be set to wherever vg1-lvroot is.  Should I manually change grub.cfg?  How can I get steps 12 and 13 working?

Thanks,
TM

---

### Post by Thaddeus Morgan on 2010-03-19
I ended up running update-grub without first chrooting to the internal drive.  In so doing, the kernels on the internal drive were discovered and are now listed as boot options when booting from the USB drive.  I rebooted with the USB drive still connected, selected a boot option on /dev/mapper/vg1-lvroot, disconnected the USB drive after booting, ran update-grub again with no errors, and ran grub-install hd0 with the following error:

# grub-install hd0
grub-probe: error: Cannot stat `hd0'
Invalid device `hd0'.
Try ``grub-setup --help'' for more information.

Instead, I tried:

# grub-install "(hd0,1)"
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda

I didn't like those warnings, so then I ran this:

# grub-install --root-directory=/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map //boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda

I'll reboot and report back soon.

---

### Post by Thaddeus Morgan on 2010-03-19
The steps in my previous post fixed the problem.  My system now boots normally.

Cheers,
TM

---

### Post by jasonsmr on 2010-03-19
Help I have a issue with my UBUNTU Lucid Install.

I did a install Of SUSE on a external and attempted to re-use my UBUNTU  system folders set in separate partitions as:
/home on partition /dev/sda5

/usr set on partition /dev/sda6

/var set on partition /dev/sda7

/tmp set on partition /dev/sda8

they can no longer be mounted in Grub?? 

please someone Help me?

well, I did an array of scans and lvm checks according to this website: [http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

first I did: 

[COLOR=#ff0000]fdisk -lu[/COLOR] then [COLOR=#ff0000]pvscan [/COLOR]then vgscan then [COLOR=#ff0000]vgchange -a y[/COLOR] then lv scan, snd thats as far as I got on vgchange -a y
it shows:

  0 logical volume(s) in volume group "tmp" now active
  0 logical volume(s) in volume group "var" now active
  0 logical volume(s) in volume group "usr" now active
  0 logical volume(s) in volume group "home" now active

  opposed to what I expected 1 logical volumes in each active.

---

### Post by Thaddeus Morgan on 2010-03-19
Hi jasonsmr,

That's a lot of information!  I don't quite follow what you're actually asking, but I'll try to answer as best I can.  Can you reformulate your questions to make them more concrete?

Yes, dm-mod should be compiled into the kernel you're using.  I'm not sure about the inner workings of LVM.

Cheers,
TM

---

### Post by jasonsmr on 2010-03-19
Well first of all thanks for the reply;

I have been researching what can be done to actually solve my problem, 

To try and clear up the problem once again:

1.) I HAD as in post hence; One clean installation of Ubuntu Lucid up and Running

    Goals would be from this information that I want to continue using this installation ;) and attempt to remedy what I had done to place things in catty-wompious status.

2.) What I did: :( --> I attempted a Installation of SUSE (an RPM based system) 

In doing so I 'experimented' a little bit without backing up my /home /usr/ and /var ,and /tmp drives!!! but ill list it anyhow.

Precisely what was done: (referring to the SUSE install.

A.)I started the installation on an external hard drive as the mounted system = [ / ] mount point. it for me was /dev/sdb (the entire drive.) I should have just used the same drive for the /home /usr /var system folders, but I didnt do that.

B.) As stated in the above 'B' step I installed root at /dev/sdb and I also proceeded to install systems folders using the LVM file system, I thought It stood for (Low Level Virtual File System) or is it Logical Volume Manager? 

Well it so happened that in the SUSE install that I could choose these drives as my folders for: /home /usr /var /tmp && better yet in the YaST installer It gave me to option NOT to format the data on the disks essentially in THEORY maintaining the working /home /usr /var /tmp directories!! 

Well I went through it like so..

      NOTE: in SUSE there version of Apt & or Synaptic= YaST is the Installation and computer management handler It walked me through how to do all this.
                  
                      1.../dev/sd5 = /dev/home = VG/home = (this drive was chosen in the Volume Group Home as home folder.Then I followed the same manner for /usr, /var, and /tmp folders..in my Ubuntu system partitions.

C.) After Installation finished with a seemingly successful Install of SUSE on a external HD with it using my Ubuntu /home, /usr, /var, and /tmp partitions in a VG (Volume groups) under LVM (Logical Volume Management) !!! All without Deleting or formating the existing data, (I checked the install log nothing on these drives {the /dev/sda} was formated) Pretty sweet right? .....................I restarted........................And .......


Oh oh!  My external HD /dev/sdb1 is no longer booting,  

{{{Later I got myPc to recognize it from the Live Cd after I install lvm2 module theN plug the USB drive in..}}}

Anyway..Grub is set to /dev/sdb?? ----> then I would simply change to a boot cd and do a sudo mount /dev/sda9 /mnt  (where my Ubuntu Lucid install is located, and manually sudo mount /dev/sda5 /mnt/home && /dev/sda6 /mnt/usr && /dev/sda7 /mnt/var $$ /dev/sda8 /mnt/tmp....then chroot into /mnt RIGHT?


Well this is where I am at, now I can not even see the LVM drives in fdisk or access them let alone from mount it just says:

mount: unknown filesystem type 'LVM2_member'

I read up on LVM file systems now,, and like my previous post says:

NOTE this is a list of commands that I tried and their results::>
_____________________________________________________________________________________
gparted shows the partitions only with a unknown fs.
____________________________________________
-->if. I install some LVM tools called to sudo apt-get install lvm2

-->then I receive the following informations from gparted.
1.) /dev/sda-->                      File System Type         Size                        Flags
                         /dev/sda5 ---lvm2                              23.3GB                  lvm
                         /dev/sda6 ---lvm2                              23.3GB                  lvm                 
                         /dev/sda7 ---lvm2                                9.3GB                  lvm
                         /dev/sda8 ---lvm2                                3.3GB                  lvm

_____________________________________________________________________________________

Question is how do I have grub recognize these partitions as drives? 

Furthermore, how do I have the ubuntu kernel && initrd recognize them as the default /home /usr /var /tmp systems folders that they are?

---

### Post by jasonsmr on 2010-03-19
Indecently on the mentioned website I followed those steps to enable the LVM system to be mounted in UBUNTU up to step 6..

________________________________________________________________________________________
THIS STEP is where things go ....diffrently for me. 
________________________________________________________________________________________
6.    Activate all volume groups available.
   [COLOR=#FF0000]# vgchange -a y[/COLOR]
 2 logical volume(s) in volume group "VolGroup00" now active
________________________________________________________________________________________
I GET THE FOLLOWING INSTEAD::
  0 logical volume(s) in volume group "tmp" now active
  0 logical volume(s) in volume group "var" now active
  0 logical volume(s) in volume group "usr" now active
  0 logical volume(s) in volume group "home" now active
______________________________________________________________________________________
I dont know what this means? besides the obvious ::My partitions are no longer recognizable as logical partitions?? 

Any help would be greatly appreciated 

NOTE By the way on step seven in the website:[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

lvscan returns nothing doing a lvscan -v returns finding all logical volumes, but nothing besides the echo from the script is returned?? what gives am I doing something wrong?

---

