---
title: "Ubuntu boots directly but not in a VM"
date: 2011-06-29
forum: General Help
---

### Post by harky on 2011-06-29
Hello,
This is probably more of a VMware problem than an Ubuntu problem, but I am hoping that perhaps someone else running Ubuntu has experienced this and/or has insight.

I have a dual-boot system running Win 7 and Ubuntu 11.04 (Both 64-bit).  I have installed VMware Player in Windows 7 and created a virtual machine which should use the partition that Ubuntu is installed on.  When I try to run the VM, the "bios" screen goes by and then I get an error message stating that "a virtual cpu has entered the shutdown state." I have tried changing the boot order to boot from cd-rom first and with the ubuntu cd in the drive, the vm will boot from cd and run.  Note that I do run VMware Player as an administrator so that it should be allowed to access the hardware directly.
 
I have tried googling for this and searching VMware communities but pretty much all I find is relative to attempts to install Mac OS X Snow Leopard.
 
Any help would be appreciated. (Note that I have a coworker who has done this successfully and we have compared notes and nothing is popping out as different from a basic configuration standpoint. We do however have different hardware as we are talking Dell Latitude Laptop (him) vs. Lenovo X201 Tablet (Me), both pretty new)
 
Thanks

---

### Post by harky on 2011-07-05
Help Please. Still looking for a way to make this work. Thanks.

---

### Post by harky on 2011-07-19
For anyone else trying to do this, here is the workaround I've found (and what I believe is the cause):

I believe the issue is caused by an inability to access the MBR since it only has a view of a single partition. After quite a bit of playing around with it, I have finally gotten it working. My solution isn't elegant and wastes a couple GB of space, but with most modern hard drives this shouldn't be an issue.

```
Solution:
1) Add a second Hard Drive to the Virtual Machine
- Go to "Edit Virtual Machine Settings"
- Choose "Add" then "Hard Disk"
- Choose "Create a new virtual disk" and configure as desired
  making large enough for an Ubuntu install
2) Load an Ubuntu install CD in your CD drive and configure the
   VM to connect to the drive at startup (or configure to use an    
   ISO)
3) Start the VM and press F2 while the VMWare "bios" screen is   
   still visible
   - It isn't up for long so you must be quick (remember to click 
     in the window first to pass mouse and keyboard input to the 
     VM)
4) Configure the VMware boot options to boot from CD first, then 
   hard drives
   - Expand the hard drives and move the SCSI device (the new 
     virtual disk) ahead of the IDE device (the physical 
     partition)
5) Save changes and exit
6) Boot from the CD and install Ubuntu to the new virtual disk
   - IMPORTANT: When Ubuntu asks what you want to do, 
     Choose "Something Else" so you can configure partitions 
     yourself.
   - Choose the device that corresponds to the new virtual disk 
     (/dev/sdb in my case)
   - In the drop down for where to install GRUB make sure you 
     choose the same device you are installing Ubuntu to (again, 
     this was /dev/sdb in my case)
7) Complete the install.
8) You should now be able to remove the CD and start the VM 
   successfully.
   - The Grub boot screen should show the newly installed linux 
     as well as the linux that is installed on your physical 
     drive.
9) Choose the linux install on the physical drive and you should 
   be good to go.
```

As I said, this isn't the most graceful solution and will waste the amount of space required to install Ubuntu on the virtual disk. I believe that more playing around with GRUB installation/configuration and the overall partitioning scheme could eliminate the need for the work around. However, I have it working and intend to leave it as is until I have some other reason that it needs to be done over again.

Hope this helps.

---

