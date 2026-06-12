---
title: "Lucid freeze during Recovery Mode bootup..."
date: 2010-06-06
forum: General Help
---

### Post by mateolargo on 2010-06-06
After upgrading to Lucid from Karmic, I was attempting to reinstall nvidia graphics drivers as they had been lost during the upgrade. There doesn't seem to be a definitive "right" way to do this, so I was trying the instructions of several forum posts.

Eventually I ran
> sudo apt-get purge nouveau*which prompted me that I was deleting important packages (not the exact wording) and made me type a sentence to confirm I wanted to do the purge. Against my better judgement, I confirmed.

After a few failed attempts of installing the NVIDIA drive, it came to me editing /etc/modprobe.d/blacklist.conf while in recovery mode and adding the following lines:

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Again the nvidia install failed. (It actually froze in the middle of the process...).

Now whenever I select non-recovery mode from GRUB, I simply get a blinking cursor and nothing happens. When I select recovery mode, it runs through a lot of initialization scripts and freezes after the following (this is the tail of the bootup scripts):

> 
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Runnings /scripts/init-bottom ...
Done.
[    3.256757] ata10: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.258062] ata10.00: ATAPI: HL-DT-STDVD-RAM GH22LS30, 1.03, max UDMA/100
[    3.259546] ata10.00: configured for UDMA/100
[    3.287836] scsi 9:0:0:0: CD-ROM     HL-DT-ST DVD-RAM GH22LS30 1.03 PQ: 0 ANSI: 5
[    3.291302] sr0: scsi3-mmc drive: 48x/48x writere dvd-ram cd/rw xa-form2 cdda tray
[ 3.291439] Uniform CD-ROM driver Revision: 3.20
[ 3.291641] sr 9:0:0:0: Attached scsi generic sg1 type 5Is there a way I can fix my Lucid install? I'm somewhat of a Linux newbie and am at a loss. I fear I screwed up something bad between the nouveau purge and then blacklisting said modules as I now have no way of even getting to a command line prompt.

Is a reinstall my only option? Can I do a reinstall over the same partition and not lose all my files/config?

---

### Post by mateolargo on 2010-06-06
Update:

I used a Lucid LiveCD, mounted my faulty installation partition, and removed the blacklist lines I had added to /etc/modprobe.d/blacklist.conf

Now when I try to launch recovery mode, it runs through the boot up scripts and goes to a blank black screen before freezing rather than freezing while still showing the tail of the boot up script.

---

