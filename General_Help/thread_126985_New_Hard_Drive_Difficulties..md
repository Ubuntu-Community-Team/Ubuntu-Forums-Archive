---
title: "New Hard Drive Difficulties."
date: 2006-02-07
forum: General Help
---

### Post by jacrider on 2006-02-07
I am running an older (ok, old) workstation.  I have a Dell Precision 410 that is about 6 or 7 years old.  I have a new 1.4GHz processor, added RAM to 1GB, so it is performing pretty well, much better under ubuntu.

I have 4 9GB scsi hard drives, which is the maximum permitted.  But I need more storage space.  I have a spare 40GB IDE drive that I am trying to install, but the BIOS (no way around this in the BIOS settings) puts this drive as the first boot device, in front of all the scsi drives and never gets to the MBR to run GRUB.

I see two solutions:  first, I can re-install ubuntu and GRUB on the IDE drive, reformat the scsi drive that houses ubuntu now and move on.  This will be a fair amount of work.  A second option that I think should be possible is to boot with the LiveCD, then create a partion on the new drive and install GRUB there.  Allow it to see my old Win2K OS and ubuntu.  With the remaining space on the IDE drive (over 39GB) I can create a ext3 partion for the storage I am trying to achieve.

Am I on to something, or should I reinstall ubuntu?

Thanks for any suggestions.

---

### Post by RAOF on 2006-02-07
I think you should be able to just install GRUB on the MBR of the new IDE hd, and have it point to your existing Ubuntu installation.  I'm not sure exactly how you would do this, though.

From browsing the grub man page, it seems you **should** be able to run the grub-install script from your existing Ubuntu installation.  You could get into your current install either with a live cd and the "chroot" command, or the "rescue" option on an install CD would also work, I think.

---

### Post by dcstar on 2006-02-08
[QUOTE=jacrider]I am running an older (ok, old) workstation.  I have a Dell Precision 410 that is about 6 or 7 years old.  I have a new 1.4GHz processor, added RAM to 1GB, so it is performing pretty well, much better under ubuntu.

I have 4 9GB scsi hard drives, which is the maximum permitted.  But I need more storage space.  I have a spare 40GB IDE drive that I am trying to install, but the BIOS (no way around this in the BIOS settings) puts this drive as the first boot device, in front of all the scsi drives and never gets to the MBR to run GRUB.
........[/QUOTE]
Most "older" PCs have external SCSI cards, which have their own boot loaders.

Try disabling booting off the IDE drive in the BIOS, and (in theory) the SCSI devices should then boot.

---

