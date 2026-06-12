---
title: "Damaged something, now have to boot with &quot;nolapic&quot; option"
date: 2010-03-21
forum: General Help
---

### Post by mjfetz on 2010-03-21
All, new to posting, but have been doing much reading in an attempt to fix my system.  A little history:  

Problem started while copying files to USB jump drive.  Not sure if I possibly forgot to unmount one or not.  System became unstable and eventually went down and would not finish a boot.  Tried everything I could find in the forums to repair and finally located my band-aid.  I added "nolapic" into the grub file and now can boot reliably, however my system only recognizes 1 cpu.  Is there a way to reload or repair local apic?  

My system is a home assembled Intel 3.2ghz dual core, MSI mainboard (P965 Neo).  Running Ubuntu 9.10 flawlessly since October 2009

Thanks to everyone for putting such great information here, any further help is appreciated.  Please let me know what additional information you need me to post to help resolve this.

Thanks
Mike

---

### Post by quixote on 2010-03-23
Well, I can't be any help with your actual question, but I doubt very much that forgetting to unmount a USB drive could cause that issue.  It could clobber the USB drive, but I think the system itself couldn't be affected.

There's got to be a way to fix lapic.  Maybe something to do with rebuilding a kernel module??

---

### Post by mjfetz on 2010-03-23
Thanks for the response.  The USB drive as of now is the only thing that I can come up with as a direct cause.  My system had loaded some updates prior, but everything was fine until I started messing with the file copies...  Rebuilding a module...  This could turn into even more of a learning experience!  

If there is any other information (log files, or whatever) that I can provide to help determine a cause/solution, please let me know.

---

