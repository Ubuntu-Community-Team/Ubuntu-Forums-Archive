---
title: "cannot burn CD's or DVD's"
date: 2011-01-30
forum: General Help
---

### Post by wordmaster on 2011-01-30
I have  a dual boot system on a box with 3.6 ghz cpu, 4 gigs memory and 3/4 terrabyte hds. I cannot get a CD/DVD to burn using Brasero. Here is the log: Well here is the last part of the log. for some reason the forum software would not let me put it all in:





BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/1990127616 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroGrowisofs
BraseroGrowisofs stopping
BraseroGrowisofs closing connection for BraseroGrowisofs
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

Any help greatly appreciated. By the way, it is not a hardware problem as I can boot into windoze and burn just fine.

---

### Post by Rogierdg on 2011-01-31
Dear wordmaster
well, as of Ubuntu 10.xx I noticed that my internal** SCSI** **CDRW drive** is only supported as **Read Only** when using Brasero or Cd/dvd creator. I cannot even blank a used CDRW anymore. An external USB CDRW (Plextor) is fully supported with no problem ! My conclusion (after a long search, and not being a Linux goeroe) is that Brasero or some of its prerequisite modules (GNOME? NAUTILUS? ..) does not support SCSI CD drives in the correct way anymore. 
With K3B however I can blank and write to my SCSI drive, but then that software does not allow me to append to an existing data project, so you can only write once, and then you have to blank before you write again.
I suggest you try K3B because I think the problem may not get a fix, since SCSI drives are old hardware.
Hope this helps or triggers other reactions.

---

### Post by wordmaster on 2011-01-31
Actually my drive is an IDE. However, I will try the K3B and see what happens. Thank you.

---

