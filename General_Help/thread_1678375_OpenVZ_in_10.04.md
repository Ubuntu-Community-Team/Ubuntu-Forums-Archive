---
title: "OpenVZ in 10.04"
date: 2011-01-30
forum: General Help
---

### Post by volvolinux on 2011-01-30
Hello 
 
I am not sure if it is the write place to create this topic, I've looked into the viutualization thread, but most of the threads are discussing how to use ubuntu in virutal box and vmware.etc.
 
I want to user OpenVZ in 10.04 and I follow the following link to do it:
 
[https://help.ubuntu.com/community/OpenVZ](https://help.ubuntu.com/community/OpenVZ)
 
the test environment is in the purge 10.04 in virutal box, everything seems well except that the system give the following warning/error information before I log into the shell.
 
----------------------------------------------------------------------------------------------------
mount:  mounting none on /dev failed: No such device
init: ureadahead main process (271) terminated with status 5
piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or usse force_addr=0xaddre
--------------------------------------------------------------------------------------------------
 
 
doesn anyone have some idea on this?
 
Thanks in advance.

---

### Post by narcisgarcia on 2011-01-31
This is the best forum for this thread:
**[Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308")**

While optimizing the tutorial we found the same warning issue, and mentioned it in this forum thread:
[http://ubuntuforums.org/showthread.php?t=1382823](http://ubuntuforums.org/showthread.php?t=1382823)
(pages 11,12)

I'm at the same point as you, but my servers are working perfectly with the "mount:" and "init:" warnings.
Your BIOS warning is specific for your box, and may also be shown with a default Ubuntu installation.

I also see your question **[here]("http://forum.openvz.org/index.php?t=rview&goto=41484&th=9349")**

---

### Post by volvolinux on 2011-01-31
Thanks a lot man! I will look into this.

---

