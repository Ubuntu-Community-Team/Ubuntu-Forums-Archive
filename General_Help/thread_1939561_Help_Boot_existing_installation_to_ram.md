---
title: "Help Boot existing installation to ram"
date: 2012-03-11
forum: General Help
---

### Post by solo16 on 2012-03-11
Anyone could show me the step by step guide of how to boot the current installation into ram?
The reason of doing this is I mainly use my minimal installation of ubuntu (10.04) with rt kernel (from tango music) for music transport server and is running serial console as well so i got all the optimization done with the kernel. 

I've already done my homework and followed the steps here: 
1) [http://www.silentpcreview.com/forums/viewtopic.php?t=48568&start=0&postdays=0&postorder=asc&highlight=ramdiskhttp://](http://www.silentpcreview.com/forums/viewtopic.php?t=48568&start=0&postdays=0&postorder=asc&highlight=ramdiskhttp://)
2) [http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/how-to-boot-os-into-ram-for-speed-and-silence-662116/](http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/how-to-boot-os-into-ram-for-speed-and-silence-662116/)
3) [http://reboot.pro/14547/](http://reboot.pro/14547/)

however I failed, when i try to boot with the custom ramboot initram img it will have error loop saying something like the file not found and you need to load the kernel first. 

I already comment out the default root partition and followed the guide from above and changed to 
none / tmpfs defaults 0 0 

I also modified the /etc/grub/grub.cfg and created a menuentry which is same as the default one except the initramfs line i changed to the one i created.

The only part i'm unsure of is the /scripts/local in the guides shown above didn't say clearly whether i should comment out or delete all of the "loop" scripts under the ### FIXME ### line and just type those new commands in. What i did is just comment out the default rootmnt line and add the new rootmnt as descripted in above sites. So am I doing right here or am i missed something here?

Cheers!!!

---

### Post by solo16 on 2012-03-12
Anyone?
Or am I posting to the wrong section? If so could direct me to the correct one?

Thx!!!

---

### Post by Mark Phelps on 2012-03-12
How about showing a little patience, OK?  We're all volunteers here and the person who knows how to do this could be, literally, on the other side of the WORLD right now.

Don't bump any more often than once every 24 hours -- it's rude.

---

