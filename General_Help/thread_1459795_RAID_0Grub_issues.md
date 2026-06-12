---
title: "RAID 0/Grub issues"
date: 2010-04-21
forum: General Help
---

### Post by k4$3 on 2010-04-21
I'll try to make this brief- Tried 10.04b2 from cd, showed my RAID 0 I use for Windows. Installed, no such luck, and I can't remember how to mount softRAID without formatting the disk. 
AND, since Windows is on RAID, how do I get grub to recognize it? 
(Yes, I'm n00b)

---

### Post by SFCampbell on 2010-05-02
K4,

I am also not a very advanced Linux user, but I may be able to offer some assistance.  I just installed the Lucid final release on my fake-RAID 0 system and like you my bootloader wouldn't recognize the array or partitions therein.  All the forums I found placed the blame on Grub2 not being soft-RAID friendly.  Whether this is or is not true, I was able to piece together a fix by replacing Grub2 with the original Grub, which steps I gathered from 2 posts:
     - [How-to Install 9.10 karmic on fakeraid]("http://ubuntuforums.org/showthread.php?t=1360445")
     - [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

The first post was very helpful but lacked critical steps, and the second contains a very long and in-depth list of options from which only a short portion applied to this process.  To simplify the process, I will try to briefly patch together the steps from these sources that fixed the problem for me:

Boot to a liveCD of the *same architecture as the install* (i386 or x64)

1) Determine which RAID partition contains your installation
     - Open a terminal window and execute these commands:
          **sudo mkdir /mnt/root**   (create a directory to mount your install)
          **ls /dev/mapper**   (get a list of partitions in your RAID array)
          * The resulting list has a common prefix which is the name of your array.  Each entry with a number at the end is *a partition*

     - To determine which of these contains your installation, do the following:
          * For each RAID partition name (such as 'nvidia_cffbdeda1') from above, mount it and check their contents with these commands
          **sudo mount /dev/mapper/{Partition Name} /mnt/root**   (mount partition)
          **ls /mnt/root**   (view contents of that partition)
          * If you recognize the filesystem as your Linux install, proceed to the next step.  Otherwise do the following:
          **sudo umount /mnt/root**   (un-mount the current partition)
          Repeat the 'mount' command above with the next partition.  Continue this process until the correct partition is identified.

2) Mount your session to the installation and log-on to the installation
     - Perform necessary mounts
          [B]sudo mount --bind /dev /mnt/root/dev
          sudo mount -t proc proc /mnt/root/proc
          sudo mount -t sysfs sys /mnt/root/sys
          sudo mount -t devpts devpts /mnt/root/dev/pts
          sudo cp /etc/resolv.conf /mnt/root/etc/resolv.conf
          sudo chroot /mnt/root /bin/bash[/B]  (Log on to the installation)

3) Remove Grub2 and install Grub
     - Prepare your installation software repo list
          **apt-get update**
     - Ensure 'dmraid' is present on your install (should already be installed)
          **apt-get install dmraid**
     - Remove Grub2 package and directory, and install Grub
          [B]apt-get purge grub2 grub-pc
          rm -r /boot/grub[/B] (remove Grub directory)
          * System will not be bootable until new bootloader is set up
          **apt-get install grub**
          **grub-install /dev/mapper/{Partition Name}**
          * Replace the brackets in this command with the partition containing your installation
          **mkdir /boot/grub**
          **cp /usr/lib/grub/{PC Architecture}-pc/* /boot/grub/**   (copy Grub files to installation)
          * Note the brackets that represent the correct PC architecture of your install.  The directory will either be "i386-pc" or "x86_64-pc" depending on your installation type.  Executing this step successfully is crucial to completing the Grub config and preventing a Grub Error #15 on reboot

4) Configure Grub device list
     **chmod 777 /boot/grub/device.map**   (make 'device.map' writable)
     **nano /boot/grub/device.map**   (edit 'device.map')
     * The entry for '(hd0)' should point to '/dev/mapper/{ARRAY Name}'
       If it has any other value (such as '/dev/sda') replace that entry to show your ARRAY NAME such as "(hd0)  /dev/mapper/nvidia_cffbdeda"
     * Be sure this entry has no number at the end, as *this would indicate a partition*.  Listing a partition will prevent Grub from loading at startup
     **chmod 744 /boot/grub/device.map**   (return permissions for 'device.map')

5) Configure Grub and affect changes:
     **grub --no-curses**   (enter Grub prompt, you will see "grub>")
     grub> **device (hd0) /dev/mapper/{Partition Name}**
     *  Enter Partition name above, *including the number* at the end of the name
     grub> **find /boot/grub/stage1**  (remember this output, you will use it in the next step)
     grub> **root (hdx,y)**  (replace 'x' and 'y' with the drive number and partition number from the step above)
     grub> **setup (hdx)**  (replace 'x' with the drive number from above)
     grub> **quit**
     # **update-grub** (generate a Grub 'menu.lst')

6) Prevent Grub from being updated
     [B]echo "grub hold" | dpkg --set-selections
     echo "grub-common hold" | dpkg --set-selections[/B]

7) Customize Grub 'menu.lst'
     **nano /boot/grub/menu.lst**  (open Grub 'menu.lst')
     * Locate *groot=(hd0,0)* and change to *groot=(hd0,x)* where 'x' is the partition number from above.  This specifies the partition where Linux is installed as the Grub Root Partition.
     * Locate the list of boot options for Ubuntu. In this list, change each *(hd0,0)* entry to show *(hdx,y)* where 'x' and 'y' with the drive number and partition number from the step above.
     Save the file and exit by pressing CTRL-X, then "Y" for 'yes', then ENTER to confirm.

Execute another **update-grub** then exit your bash session and terminal by entering **exit** (probably twice).  Reboot the machine.  

Your bootloader should come up after POST.  Confirm each OS boot option (Windows, Ubuntu, etc) work to load the correct partition.  If any are incorrect you can edit the boot option when the Grub menu comes up by pressing '**e**' twice and change the partition number then **ENTER** to confirm and '**b**' to try booting that partition.  Try each partition number in order to identify the correct one.  Once identified, you can modify the Grub 'menu.lst' using the command listed above and change it permanently.

I hope this works for you, but at the same time I hope you only ever have to do it once!  If Grub2 really lacks the fake-RAID capability hopefully it will be corrected in the near future.

---

