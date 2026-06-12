---
title: "RAID1 rebuilding nightmare"
date: 2009-12-01
forum: General Help
---

### Post by JohnUt on 2009-12-01
I had another HD come up with bad sectors in my RAID1.  So I pulled out the bad sector drive and put the new drive in.  With the single working RAID1 drive with the data in the computer it failed to boot.  I installed the new drive and manually copied everything from the old drive over via a Gparted Live CD.  Still no booting.  Kind of scratching my head here as I can see that both of the drives have data on them but are unable to get them to boot.  I tied unplugging each of the drives one at a time and booting the system but no luck there either.

I used a live CD and couldn't even manually mount either of the drives, which I thought was really odd.

I need to find someone to pay me to be a beta tester.  I have proven numerous times that I can really break obscure things in innovative ways that's for sure. ;)

---

### Post by Aearenda on 2009-12-02
I suspect you won't get a proper answer without supplying a good deal more info, like any good beta tester :-) 

When you say the computer failed to boot, what exactly happens? Does it actually start the Linux kernel, or fail in Grub? What error message does it show?

Is your RAID done with the BIOS or with software in Linux?

If is a software RAID, then be aware Linux does this at partition level. This means that the boot sector does not get copied to both drives, and Grub typically only gets installed on one of the drives. Do you recall doing anything special about this?

To mount the partitions on the live CD you'll need to use different commands to normal, assuming this is a software RAID1.

---

### Post by sdowney717 on 2009-12-02
try looking thru this
instructions are for grub 0.97 not grub2 1.97

what you are doing is setting up raid1 again due to the faulty drive

[http://www.linuxconfig.org/Linux_Software_Raid_1_Setup](http://www.linuxconfig.org/Linux_Software_Raid_1_Setup)

---

### Post by JohnUt on 2009-12-02
> **Aearenda said:**
> 
When you say the computer failed to boot, what exactly happens? Does it actually start the Linux kernel, or fail in Grub? What error message does it show?

"Verifying DMI Pool Data ..............." and stays there forever never making it to the kernel.

> Is your RAID done with the BIOS or with software in Linux?

A software raid.

> If is a software RAID, then be aware Linux does this at partition level. This means that the boot sector does not get copied to both drives, and Grub typically only gets installed on one of the drives. Do you recall doing anything special about this?

I had the drive with the GRUB fail as it would boot up normally before and not since replacing the drive

---

### Post by Aearenda on 2009-12-02
Was this a new installation with Grub 2, or does it still have the old Grub installed (typically being an upgrade in place from an earlier version)?

EDIT: From Googling around I suspect the way to go in a nutshell is to get your second drive booted using the [System Rescue CD]("http://www.sysresccd.org"), which has RAID tools pre-installed. I'm not sure whether the Ubuntu LiveCD does. The server CD might. 
After it has booted, I would try to chroot into the now-active but degraded system, and use its installed grub to install the boot sector on the remaining drive. After that, it should be possible to reboot from the remaining drive. Of course, the devil is in the detail here.

If it were me I would use another machine to set up a matching system in VirtualBox, and then simulate the error, to work out the steps to take on the real one.

---

