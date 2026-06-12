---
title: "quick ?? on ubuntu install"
date: 2012-02-09
forum: General Help
---

### Post by Nihilithik on 2012-02-09
just a quick question, to continue on [http://ubuntuforums.org/showthread.php?t=1922233](http://ubuntuforums.org/showthread.php?t=1922233)

i've noticed that when i boot up in bios, i have an option to choose which drive to boot from. when i select my drive that is blank, i get bootmsgr not there. can i just select that and boot from a live usb, instead of actually unplugging the drive if i want to install ubuntu on said drive?

---

### Post by drmrgd on 2012-02-09
> **Nihilithik said:**
> just a quick question, to continue on [http://ubuntuforums.org/showthread.php?t=1922233](http://ubuntuforums.org/showthread.php?t=1922233)

i've noticed that when i boot up in bios, i have an option to choose which drive to boot from. when i select my drive that is blank, i get bootmsgr not there. can i just select that and boot from a live usb, instead of actually unplugging the drive if i want to install ubuntu on said drive?

It should be just as simple as selecting the device that contains the bootable Live CD and booting from that.  If you try to boot to a blank drive, you'll just get stuck with the error you described.  So, select the USB drive that has your ISO on it.

---

### Post by Nihilithik on 2012-02-09
"Easy.

Just install ubuntu with your windows drive unplugged

afterwards hook it back up, boot ubuntu and run update grub"

... i am trying to avoid this. actually digging out the hard drive with windows 7 on it. 

However if i am understanding you right, it doesn't matter, i should be able to see both drives when i load from the iso, and be able to choose which one to install, then boot ubuntu from?

---

### Post by hildenbrandsteven on 2012-02-09
It should see both drives, but if you set it to boot first from the drive containing the LiveCD, you shouldn't run into any problems.

---

### Post by drmrgd on 2012-02-09
> **Nihilithik said:**
> "Easy.

Just install ubuntu with your windows drive unplugged

afterwards hook it back up, boot ubuntu and run update grub"

... i am trying to avoid this. actually digging out the hard drive with windows 7 on it. 

However if i am understanding you right, it doesn't matter, i should be able to see both drives when i load from the iso, and be able to choose which one to install, then boot ubuntu from?

Yeah.  When you choose the install Ubuntu selection, you should eventually get to a point when it wants to know where to put it and if you want to have it automatically partitioned or manually.  I usually choose manually and partition from there.  Either way, though, it should ask at that point which drive you want to install Ubuntu to.  Just be careful that you don't choose the wrong one and overwrite your Windows 7 drive by mistake!  I think people unplug the Windows drive (in part) just to be sure that they don't choose the wrong one and overwrite it.

---

### Post by Nihilithik on 2012-02-09
Cool. Thank you very much O'Guru's De Unbutuz!!

---

