---
title: "How do i find this drive?"
date: 2010-11-30
forum: General Help
---

### Post by donextintor on 2010-11-30
How do i find my dvd writer drive that i installed? It shows up that my hard drive recognizes that its hooked up on the black screen that comes up when first turn on computer. But when i go to my computer it just have the cd drive available.

What do i do?

---

### Post by Hippytaff on 2010-11-30
what is the output of
```

df

```
and
```

lspci

```
in the terminal?

---

### Post by tlroche on 2010-11-30
Something else that might be helpful to run from the terminal:

```
sudo lshw -C disk
```

---

### Post by donextintor on 2010-11-30
output of df is as follows:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36955720   3953212  31125212  12% /
none                    256536       220    256316   1% /dev
none                    262132       700    261432   1% /dev/shm
none                    262132       212    261920   1% /var/run
none                    262132         0    262132   0% /var/lock
/dev/sdb1              7813184   3901172   3912012  50% /media/031C-2054
/dev/sdc1            488384000 271287120 217096880  56% /media/FreeAgent Drive

output of lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

---

### Post by Hippytaff on 2010-11-30
> 
/dev/sdb1              7813184   3901172   3912012  50% /media/031C-2054
/dev/sdc1            488384000 271287120 217096880  56% /media/FreeAgent Drive
It's one of these I think...try putting a dvd in the drive and CD'ing to it
```

cd /media

``````

ls -a

```to see if ubuntu can see it :-)

you might need to mount it if it none of these

---

### Post by donextintor on 2010-11-30
output of sudo lshw -C disk:

PCI (sysfs)  
  *-disk                  
       description: ATA Disk
       product: WDC WD400EB-75CP
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 06.0
       serial: WD-WMAAT7900649
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000b2071
  *-cdrom
       description: CD-R/CD-RW writer
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw
       configuration: status=open
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 7650MiB (8021MB)
       capabilities: partitioned partitioned:dos
  *-disk
       description: SCSI Disk
       product: FreeAgent
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 0138
       serial: 2HC015KJ
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=51b922fe


its showing everything but the dvd writer yet when i start up my computer it says that the dvd writer is there

---

### Post by AlphaLexman on 2010-11-30
> **Hippytaff said:**
> It's one of these I think...

If everything is sata and not ide, 'sda1', 'sdb1', and 'sdc1' are all the first partition on hard drives.

On my machine /dev/sr1 points to /media/cdrom0

Post the output of:
```
mount
```

---

### Post by donextintor on 2010-11-30
the freeagent is my external hard drive i have no thats what came up when just did the cd /media and ls -a

---

### Post by Hippytaff on 2010-11-30
I missed a very important point mentioned by alphalexman - but like I said if it none of these you might need to mount it :-)

check with alphalexmans suggestion
```

mount

``` :-D

---

### Post by matt_symes on 2010-11-30
Hi

Does the DVD drive has a disc in it? It will not auto mount it until it does. If it's not auto mounting then you can use gconf-editor or gconf-tool to set this up in gnome.

Put a disc in it and it should auto mount. If i have miss understood you, i'm sorry.

Kind regards

---

### Post by donextintor on 2010-11-30
output of mount:

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/silky/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=silky)
/dev/sdb1 on /media/031C-2054 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdc1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


and now i have to go to work boooooo

---

### Post by AlphaLexman on 2010-11-30
The optical drive is NOT mounted, when you get off work, post the output of:
```
cat /etc/fstab
```
although I'll be in bed ;-)

---

### Post by pricetech on 2010-11-30
The screen with the black background is your computer's POST screen by the way.  Seeing the drive listed there means the BIOS has found it, which is a good first step.

As others have mentioned, put a disk in the drive and see if it auto mounts.  It should, but you won't find it if there's no disk in the drive.

---

### Post by donextintor on 2010-12-01
the output of cat /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=847a4a15-40e2-4b3f-a6e2-84690945907b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e5c72619-374d-49bd-b6f3-2e898957bf9a none            swap    sw              0       0


i put a dvd in and nothing happens

---

### Post by AlphaLexman on 2010-12-02
You will need root privileges to put a line like this in '/etc/fstab'
```
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
Your dvd may be '/dev/scd0' or something else. Check 'man fstab' for the other options.

---

### Post by donextintor on 2010-12-04
i dont understand what you are telling me to do with that one im a little new at this

---

### Post by Penguin=) on 2010-12-04
> **Hippytaff said:**
> I missed a very important point mentioned by alphalexman - but like I said if it none of these you might need to mount it :-)

check with alphalexmans suggestion
```

mount

``` :-D

how do you do the /code thing?

---

### Post by AlphaLexman on 2010-12-04
> **Penguin=) said:**
> how do you do the /code thing?

The toolbar above the box you type in, you will see icons for: **Bold,** *Italics,* _Underline,_ etc...

The icon that looks like a " # " will insert the /code brackets for you.

---

### Post by donextintor on 2010-12-04
i already tried mount and posted the reports

---

### Post by AlphaLexman on 2010-12-04
I'm sorry, my previous post was in response to penguin=) although slightly off topic...

First, we want to figure out which device your machine identifies with your new DVD drive.

In a terminal, type:
```
eject /dev/scd0
```

If you have more than one optical drive, and the wrong bay opened do:
```
eject /dev/scd1
```

If one of those worked, then:
```
gksudo gedit /etc/fstab
```
enter your password when asked...

and copy:
```
/dev/scd[COLOR="Red"]0[/COLOR] /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
to the end of the file, and save it.

NOTE: use the number 0 or 1 of the 'eject' command that worked above in place of the red '0'

You will need to logout, and login for the changes to take.

---

### Post by donextintor on 2010-12-16
results of /etc/fstab:



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=847a4a15-40e2-4b3f-a6e2-84690945907b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e5c72619-374d-49bd-b6f3-2e898957bf9a none            swap    sw              0       0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by AlphaLexman on 2010-12-16
It has been a while since we have seen the output of:
```
mount
```
Please post the most recent version based on the changes from this thread and other updates you have.

---

### Post by donextintor on 2010-12-17
results of mount

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/silky/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=silky)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by AlphaLexman on 2010-12-17
Did you confirm the '/dev/scd1' as your dvd drive?
If not, did you try '/dev/scd0' in /etc/fstab?

---

### Post by donextintor on 2010-12-17
when i  put /ect/fstab in the terminal it say permission denied

---

### Post by AlphaLexman on 2010-12-18
You need super-user permission to edit that file:
```
gksudo gedit /etc/fstab
```

---

