---
title: "Firewire to transfer files between two computers"
date: 2011-12-20
forum: General Help
---

### Post by Zachary123 on 2011-12-20
Hi, I posted in the Absolute Beginner forum because I am one, but got no replies possibly because this isn't a beginner topic?

Just installed MythBuntu on an old Shuttle PC and I have been using Samba to transfer files.  However, it is pretty slow (1.2MiB/s) and I have quite a bit of audio files to transfer (50GB).  I want to use firewire connections to transfer the files more quickly.

I used these posts to help me but I have ran into problems very early:

[http://stream-recorder.com/forum/connecting-two-ubuntu-9-10-computers-over-t5347.html](http://stream-recorder.com/forum/connecting-two-ubuntu-9-10-computers-over-t5347.html)

[https://help.ubuntu.com/community/EthernetOverFirewire](https://help.ubuntu.com/community/EthernetOverFirewire)

[http://ubuntuforums.org/showthread.php?t=1766336](http://ubuntuforums.org/showthread.php?t=1766336)


From step 1 I edited the file but in step 2 when I enter the command I get an error:

**FATAL: Module eth1394 not found.**

Although I was able to enable the ohci1394 firewire controller driver using **sudo modprobe ohci1394**

Do I need to restart the computer and boot with the firewire?  If so, do I just move the firewire to 1 in the BIOS boot order?

Thanks,
-Z

---

