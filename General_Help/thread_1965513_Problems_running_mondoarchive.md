---
title: "Problems running mondoarchive"
date: 2012-04-25
forum: General Help
---

### Post by OrchidStar on 2012-04-25
I installed MondoRescue on my Ubuntu 10.04 system.

**apt-get install mondo**

I want to create an iso file and save it to a DVD. My problem is that I can't run mondoarchive.

**sudo mondoarchive**
Initalizing....
Execution run ended; result =-1
Type 'less /var/log/mondoarhchive.log' to see the output log

---
**cat mondoarchive.log**

 [FONT=&quot]...ran with res=256
[TH=8514] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sda

No, Schlomo, that doesn't mean /dev/sda is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=8514] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
      [TH=8514] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /3%/mondo.tmp.0NQmdk for Mondo.
      [TH=8514] libmondo-files.c->register_pid#815: Unregistering PID
      [TH=8514] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256

 [/FONT]
  From the looks of this errors in the mondoarchive.log it looks like I have several errors. I have dvd+rw-toos as well cdrecord. 

****

Thanks in advance!

---

### Post by crossy on 2012-06-19
I ran into the same problem just now (backing up my 10.04LTS ready to jump to a new 12.04LTS install) and found your post.

According to Bruno Cornec (mondo's project lead) the issue is that the release that ships with Ubuntu is "broken". So after _deinstalling_ mondo and mindi I followed the update process given at 
[http://trac.mondorescue.org/wiki/FAQ#Q11DoesmondoworkwithDebianUbuntudistributions]("http://trac.mondorescue.org/wiki/FAQ#Q11DoesmondoworkwithDebianUbuntudistributions") and followed up with a "sudo apt-get update; sudo apt-get upgrade" combination.

After that it was dead easy to install a version of Mondo that appears to work!

Well, actually, I got a warning about unauthenticated updates, but just accepted the risk. Later on I actually READ the whole post and saw the bit about adding the key to the apt keyring. *Oops!*

Hope this helps.

---

