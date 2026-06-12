---
title: "Failed to Install boot loader please help"
date: 2011-06-28
forum: General Help
---

### Post by Gr.Turtle on 2011-06-28
Long time fan first time poster!
The Ubuntu forums have been helpful to me without posting for the past 3 years, but I've hit a wall with this one.

I recently bought a used PC and ditched win7 for Ubuntu 11.04. My initial install of Ubuntu was flawless, but suddenly the mouse over for newly opened windows would not register, only clicking the icons on the window below it.  The computer slowed to a crawl, and I decided to take a loss on all of the files and try a fresh install. 

After numerous attempts I am stuck at the Grub install stage. I continued the instillation without a boot loader but I can't figure out how to manually install grub, or if sda is the proper drive to mount. Any help will be greatly appreciated.

---

### Post by drs305 on 2011-06-28
Gr.Turtle

Hopefully your post will lead to successful booting of your system.  

If you know the Ubuntu partition and can boot a LiveCD, you can try this simple step. It doesn't install *all* the Grub2 files, but if you are just missing some it may solve your problems.

Boot the LiveCD and mount your Ubuntu partition. I will use sda1 as the example. Change as needed.

```
sudo mount /dev/sd**a1** /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```
Do NOT use the partition number in the second command. Reboot and see if it boots (without the CD).

If it needs a complete install of Grub 2, you will need to chroot into your real installation and install Grub 2. But if you can't boot, before doing this please download, extract and run the boot info script from the following site. It will create a RESULTS.txt file - post the contents of that file so we can see the status of your boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by seawolf167 on 2011-06-28
[Here is the how-to ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")for reinstalling GRUB2 (echoing drs305's post) with the commands, some images and explanations.

---

### Post by drs305 on 2011-06-28
> **seawolf167 said:**
> [Here is the how-to ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")for reinstalling GRUB2 (echoing drs305's post) with the commands, some images and explanations.

lol. I didn't realize the Boot Repair tool had been added to the Grub2 community doc, on which I did a major revision just a few weeks ago. 

By all means, try using the Boot Repair tool and see if it works for you.

---

### Post by lakosshoots on 2011-06-28
Hi there. My suggestion is to run Ubuntu from live CD or USB and check HDD for errors. Normally it should be a problem to install ubuntu. I suspect it is a faulty HDD. Run disk utility to check it. Otherwise check the post from the master "drs305"

Good luck

---

### Post by Gr.Turtle on 2011-06-28
Upon restart i came into a grub prompt. Will post .txt file following instructions shortly

---

### Post by Gr.Turtle on 2011-06-28
results attached

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   621,473,791   621,471,744  83 Linux
/dev/sda2         621,475,838   625,141,759     3,665,922   5 Extended
/dev/sda5         621,475,840   625,141,759     3,665,920  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6a952398-3a03-4a40-90c3-3aab6ea4424d   ext4       
/dev/sda5        5596a189-27cb-45da-99cf-31db3202d945   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6a952398-3a03-4a40-90c3-3aab6ea4424d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5596a189-27cb-45da-99cf-31db3202d945 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 166.135231018 = 178.386345984  boot/grub/core.img                             1
   1.255104065 = 1.347657728    boot/initrd.img-2.6.38-8-generic               2
 166.133281708 = 178.384252928  boot/vmlinuz-2.6.38-8-generic                  1
   1.255104065 = 1.347657728    initrd.img                                     2
 166.133281708 = 178.384252928  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Gr.Turtle on 2011-06-28
trying to install the grub tool ended in this

(Reading database ... dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gnome-power-manager': Input/output error

---

### Post by drs305 on 2011-06-28
Grub, as you noted, isn't completely installed. You can try to use the Boot Repair Tool to try to install it or use the following series of commands. It will do via GUI what I write below, although you will have to enter a command or two.

If using the terminal from the LiveCD, you will have to 'chroot' into your Ubuntu installation to allow the commands to act upon your real installation. I'll include the purge command as well just to make sure any errors are removed.

I'll explain what the commands do, but for more information you can click on the 'Chroot' link in my signature line. It goes into more detail.

```

sudo mkdir /mnt/temp # Make a temporary directory
sudo mount /dev/sda1 /mnt/temp  # Mount your real Ubuntu partition
# The following commands mounts system files
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp # Chroot into your real partition
# You should now be at a root prompt. Sudo is no longer used.
apt-get update   # Make sure Internet is working. If not, STOP HERE.
apt-get purge grub-pc grub-common  # Purge Grub 2
apt-get install grub-common grub-pc # Install Grub 2
# ^^ Tab to OK for the first screen and press ENTER. On the next screen, tab to sda and press the SPACEBAR to place an asterisk next to it. Do not select sda1. TAB to OK and ENTER.
update-grub
exit # Exit chroot
# Unmount filesystems
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
sudo umount /mnt/temp

```

Reboot.

Note: It's possible that once you get into the chroot all you would have to do is run: "update-grub" to create the grub.cfg file, but executing the other steps while in chroot will give you the best chance of having to do this procedure only once.

---

### Post by Gr.Turtle on 2011-06-28
Followed instructions. Ubuntu booted. This is why I love this community. Many Many thanks... marking as solved!

---

### Post by drs305 on 2011-06-28
Gr.Turtle 	

:-)

Glad it's working and also appreciate you marking the thread 'Solved'.

Did you happen to try the Boot Repair Tool? It was introduced a few months ago and some of us that deal with Grub2 problems on a regular basis are still trying to get a feel for how well it works and meets the needs of users. Thanks in advance for any input you provide.

---

### Post by Gr.Turtle on 2011-06-28
I attempted the repair tool from live cd. The install worked until the last command which gave me this error message at the end of the script

(Reading database ... dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gnome-power-manager': Input/output error

Sorry, I didnt copy the full text.

---

