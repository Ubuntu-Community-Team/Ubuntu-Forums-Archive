---
title: "Hanging at Blinking Cursor _ on System Boot"
date: 2011-03-15
forum: General Help
---

### Post by blacksunseven on 2011-03-15
Hey all,

After some moving around of internal HDs and SATA cables, I attempted to start up my Ubuntu computer only to find it hanging at the _ blinking cursor screen. I have tried several methods of troubleshooting which include unplugging all drives minus the system drive, running the bootinfo script that's floating around here to verify grub is installed in the right place on the right drive (it is), restoring my original HD configuration. I can't really figure out what the problem is and it's driving me crazy. I CAN, however, boot to a liveCD distro without a problem so I'm hoping some guru out there knows how I can fix my issues here.

extra info: my fstab is configured to use UUIDs and none of the actual drives have changed, just where the cables were routed.

---

### Post by rmaultz on 2011-03-16
Sounds like the boot loader  is working  but it is unable  to locate the boot  sector of the hard drive  i have dealt with  this before  when my bios is not set to the correct hard drive for boot please verify the bios is set to correct hard drive to boot as you stated earlier you moved cables around  unless you place it back  to the original  arrangement  the system will stay at blinking cursor  waiting for you to point it to the correct boot  drive 


*** Blinking cursor means it cannot find the os on the partition listed  in grub probably due to the hard drive being on a different  sata  or ide channel  after moving the drives .

---

