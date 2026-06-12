---
title: "Can see esata card but no disks"
date: 2011-03-02
forum: General Help
---

### Post by garethsimpsonuk on 2011-03-02
Hi,

I've just purchased a PCI-E 2 port controller card for backups. The problem is that the card is picked up using lspci but the drives arent being detected.

I have tested drives, cables and docks using another card so I know they are fine.

Card - PEXESATA2
Chipset - SiI3132

Output of lspci

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 SCSI storage controller: Marvell Technology Group Ltd. 88SX7042 PCI-e 4-port SATA-II (rev 02)
03:00.0 SATA controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

```

I assume that because its picked up correctly then it should be working fine but I found some drivers @ [http://us.startech.com/product/PEXESATA2-2-Port-PCI-Express-eSATA-Controller-Card](http://us.startech.com/product/PEXESATA2-2-Port-PCI-Express-eSATA-Controller-Card)

Included drivers are for Fedora and RedHat. Is it possible to get these to work with 10.10? Included are 2 /img files and 2 read me's pasted below:

```

Silicon Image Fedora Red Hat Series Driver Installation
               (SATA 3132 Controller) 
 

OVERVIEW

This driver disk adds support for the SiI 3132 SATA controller that is otherwise
not supported by the open source installation program.

   Supported versions:

      * Fedora Core 4, Kernel revision 2.6.11-1.1369_FC4.
      * This driver rev. 1.0.6.0 supports 64-bit AMD/Intel platforms for Sii3132 controller with base (non-RAID)
        port multiplier and hot-plug capabilities.

CREATE FLOPPY before INSTALLATION
    
A floppy disk is required to install into a brand new (or blank) disk drive. 

1.  Several Options:
 
  . If you received a zip file, Use Winzip to unzip the [distribution]filename.zip file on to a formatted floppy disk.
  . If you received a tgz file, extract the contents of the [distribution]_sii____rhdd.tgz file on to a
    formatted floppy disk. (e.g. use tar xzf [distribution]_sii____rdhh.tgz)
    
  . If you received a img file, and you are running windows: use "rawrite.exe sii____.img A:" 
    (you can get rawrite from RedHat installation disk #1 \dosutils directory)
    If you are running linux:  use "dd if=filename.img of=/dev/fd0"
  

  Note: IMPORTANT NOTE FOR OEM CUSTOMERS
        ADD your PCI ID to the "pcitable" file if OEM VendorId is going to be different 
        from SiI 0x1095 IDs. (End Users should ignore this step) 

 
2. The following BIOS BOOT sequence is recommended => CD, Hard Disk,
   Floppy
  

INSTALL THE Fedora DRIVER

 Before you start make sure the BIOS sees your adapter card (if applicable) and
 your disk drives.

 Installing the Fedora SiI Driver currently requires some manual intervention.

 If just adding Data Drives or upgrading go to sections 2.1 or 2.2
     (non-bootable SATA drives are considered Data Drives)
    
 Boot from the Fedora CD 1 or a boot diskette that you have created.
 At boot time type:
   'linux noprobe' at the boot prompt.

 When you get to the  screen shown in figure 1. get a shell prompt (see last page) and execute the initial_install script
 as follows:


# mkdir /f   
# mount /dev/fd0 /f
# cd /f
# ./initial_install.sh



figure 1:

             | Warning |

    No hard drives have been found.
    You probably need to manually
    choose device drivers for the
    for the installation to succeed. Would
    you like to select drivers now?

        | Yes |           | No |                   
            



 Once the driver is installed select 'No' and then 'Done' on the next screen. 
 Continue with the installation. Last,  BEFORE REBOOTING run the script below.

# ./upgrade_driver.sh


This last step writes all the drivers permanently into the kernel. 

Installation at this point is completed.


2.1  Adding a DATA DRIVE 
    
     If your system is already up and running then you can use execute shell scripts to modify
     the kernel or add loadable modules to access the SATA drives as follows:


     . # mount /mnt/floppy
         in case of DOS formatted floppy
         . # mount -t vfat /dev/fd0 /mnt/floppy  
     
     . # 'sh /mnt/floppy/load-driver-from-floppy.sh'  (DATA DRIVES)  
         or

       If you received a zipped file, unzip the file and copy the modules.cgz
       to a destination directory. Type "modules.cgz | gunzip | cpio -ivH crc" to
       unzip the driver tree and load the appropriate driver file to your system.

    . if you want to make sure you can see the drives, you may want
       to 'mke2fs /dev/sda' and 'mount /dev/sda /test' the hard disk(s).
       (Depending on your system configuration, the SATA drives could be /dev/sdb, /dev/sdc, /dev/sdd.....) 

     . insmod sii3132. As an example add the following lines at the end
       of the script in /etc/rc.d/rc.sysinit

       'insmod scsi_mod'
       'insmod sii3132'

     . At this point you are done with the installation 
                             
2.2  Upgrading the Kernel

     If your system is already up and running then you can use execute shell scripts to modify
     the kernel or add loadable modules to access the SATA drives.


3.   GENERAL INFO

   . If you cat /proc/scsi/sii3132/* you should see the Driver as reported by
     the kernel.

   . If you cat /proc/scsi/scsi you should see the your DRIVE TYPE as reported
     by the kernel.


4. New Features and bug fixes

   Initial release of FC4 Si3132 legacy raid driver.
   The driver could support SATA ATAPI devices.
   This revision of driver has GUI interface that can configure RAID set.


5. Known Restriction

   Please note that ATAPI hot plug is not expected.


Console Keystrokes Contents 

1 [Ctrl]-[Alt]-[F1] installation dialog 
2 [Ctrl]-[Alt]-[F2] shell prompt 
3 [Ctrl]-[Alt]-[F3] install log (messages from installation program) 
4 [Ctrl]-[Alt]-[F4] system-related messages 
5 [Ctrl]-[Alt]-[F5] other messages 
7 [Ctrl]-[Alt]-[F7] X graphical display


```

```

#######################################################################
#         Silicon Image SiI SATA controller                           #
#               RedHat Linux  Driver     	                      #
#######################################################################


1. OVERVIEW

   This driver disk adds support for the SiI 3132 SATA controller and overrides the Open Source Driver if it is contained in the CD-ROM.

   Supported RedHat Linux versions:

      * RedHat Enterprise Linux 4 Update 1, Kernel revision 2.6.9-11.
      * This driver rev. 1.0.6.0 supports 64-bit AMD/Intel platforms for Sii3132 controller with base (non-RAID) port multiplier and hot-plug capability.


2. INSTALLATION

   For detailed information about RedHat installation visit:
    http://www.redhat.com/docs/manuals/

   IMPORTANT NOTE FOR OEM CUSTOMERS:
        ADD your PCI ID to the "pcitable" file if OEM VendorId is going to be different 
        from SiI 0x1095 IDs. (End Users should ignore this step.) 

   2.1 PREPARING DRIVER DISK

   A floppy disk is required to install into a brand new (or blank) disk drive. 

   If you received the driver in an xxx.img format, create a floppy containing the drivers under Linux by 'dd' as follows:

      dd if=file_name.img of=/dev/fd0  (In a Linux System)
      where filename will change with the distribution used.
       
   If you received a zip file, Use Winzip to unzip the [distribution]filename.zip file on to a formatted floppy disk.

   2.2 FRESH INSTALLATION TO A BOOT DRIVE

   Before you start make sure the BIOS sees your adapter card (if applicable) and
    your disk drives.
    
   If just adding Data Drives or upgrading, go to sections 3 or 4.
     (Non-bootable SATA drives are considered as data drives.)

   The following BIOS BOOT sequence is recommended => CD, Hard Disk, Floppy.
 
   Installing the SiI Driver currently requires some manual intervention.
   Boot from the CD 1.

   When you get to the screen shown in figure 1, get a shell prompt ([Ctrl]-[Alt]-[F2]) and execute the initial_install script as followings to install the driver for boot disk:


   # mkdir /f   
   # mount /dev/fd0 /f
   # cd /f
   # ./initial_install.sh



                    Figure 1:


                    | Warning |

         No hard drives have been found.
         You probably need to manually
         choose device drivers for the
      for the installation to succeed. Would
      you like to select drivers now?

        | Yes |                        | No |                   
               



   Once the driver is installed select  'No' and then 'Done' on the next two screens.      Continue with the installation and follow the system instructions and swap the CDs as directed.

   At the end,  go to shell prompt ([Ctrl]-[Alt]-[F2]) to run the script below BEFORE REBOOTING.

   ./upgrade_driver.sh 


   This last step writes all the drivers permanently into the kernel.

   Go back to the last screen (such as [Ctrl]-[Alt]-[F7]) to reboot the system. Installation of boot disk at this point is completed.

   Please note, all ATA/ATAPI devices connected to SiI controller will be presented as SCSI devices.


3. ACCESS A SATA DISK AS DATA DRIVE WITHOUT UPGRADING THE KERNEL	
    
     If your system is already up and running, you can add loadable modules to access the SATA drives by the followings:

     . Unload the open source driver for Silicon Image controllers if it was loaded.

     . # mount /mnt/floppy or mount /media/floppy, whichever is appropriate.
          in case of DOS formatted floppy
          . # mount -t vfat /dev/fd0 /mnt/floppy  
     
     . Type "modules.cgz | gunzip | cpio -ivH crc" to
       unzip the driver tree and select the appropriate driver file for your system.
     
     . Install the driver by adding the following lines at the end of the script in /etc/rc.d/rc.sysinit

       'insmod scsi_mod'
       'insmod sii3132'

     The SATA data drive would be available at next time when system reboot. At this point you are done with the installation 

     . If you want to permanently have access to your SATA drives we recommend
       you upgrade to kernel as shown below.
   


4. UPGRADE THE KERNEL TO ACCESS SATA AS DATA DRIVES

     If your system is already up and running, you can use shell scripts to modify
     the kernel or add loadable modules to access the SATA drives as followings:

     . Unload the open source driver for Silicon Image controllers if it was loaded.

     . # mount /mnt/floppy or mount /media/floppy, whichever is appropriate.
         in case of DOS formatted floppy
         . # mount -t vfat /dev/fd0 /mnt/floppy  

     . # 'sh /mnt/floppy/load-driver-from-floppy.sh'  (DATA DRIVES)  
         (or use the the proper script depending on your kernel)

     . If you received a zipped file, unzip the file and copy the modules.cgz
       to a destination directory. Type "modules.cgz | gunzip | cpio -ivH crc" to
       unzip the driver tree and load the appropriate driver file to your system.

     . if you want to make sure you can see the drives, you may want
       to 'mke2fs /dev/sda' and 'mount /dev/sda /test' the hard disk(s)

     . insmod sii3132. As an example add the following lines at the end
       of the script in /etc/rc.d/rc.sysinit

       'insmod scsi_mod'
       'insmod sii3132'

     . # ./mnt/floppy/upgrade_driver.sh
          /etc/lilo.conf and /boot/grub/grub.conf will be saved by the setup
          script. You may back them up as you wish. Visually inspect lilo.conf and 
          grub.conf to make sure the result is what you want.
   
5.   GENERAL INFO

   . If you cat /proc/scsi/Sii3132/* you should see the Driver as reported by
     the kernel.

   . If you cat /proc/scsi/scsi you should see the your DRIVE TYPE as reported
     by the kernel.


6. New Features and bug fixes

   Intial driver release for RHEL 4 Update 1.
   The driver could support SATA ATAPI devices.
   This revision of driver has GUI interface that can configure RAID set.


7. Known Restrictions

   Please note that ATAPI hot plug is not expected.


Console Keystrokes Contents:

1 [Ctrl]-[Alt]-[F1] installation dialog 
2 [Ctrl]-[Alt]-[F2] shell prompt 
3 [Ctrl]-[Alt]-[F3] install log (messages from installation program) 
4 [Ctrl]-[Alt]-[F4] system-related messages 
5 [Ctrl]-[Alt]-[F5] other messages 
7 [Ctrl]-[Alt]-[F7] X graphical display


```

Or is the card already working and the issue lies elsewhere?

Any help is appreciated.

---

### Post by grahammechanical on 2011-03-02
It is my guess, and I could most definitely be wrong, that if the card is recognized by lspci command then there are drivers for it in the kernel.

Check to see if the card is detected in the BIOS or enabled. I guess, again, that it would not be showing up in lspci if it was not detected in the BIOS, but it may not be enabled.

What do you see when using Disc Utility? I see a line for floppy drive. I do not have one connected but I do have a hardware device for using a floppy drive. So, you should see this PCI-E adapter in Disc Utility. It is possible that this utility might give you the option to mount these drives.

Regards.

---

### Post by garethsimpsonuk on 2011-03-03
Just to let you know I managed to fix this highly technical problem... I'd plugged the cable in the wrong port.

Thanks for your help, unfortunately no amount of open source community assistance is going to overcome me being a muppet!

---

