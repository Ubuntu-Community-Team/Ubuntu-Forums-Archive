---
title: "boot problem [7.xxxxxxx] not responding"
date: 2010-03-25
forum: General Help
---

### Post by Lunch2000 on 2010-03-25
I searched the forums for this issue and could only find one thread that seemed related but it did not address my needs. Sorry if this is a repost.
 
 
 
I am runing Ubuntu 8.10 64-bit using Grub 1.5, have not updated recently nor made a major config change. I just started having a really strange boot issue that started today. Everything was working fine yesterday and I shutdown normally. When trying to boot up my machine today Grub would start, it would identify my boot drive and begin booting. However after about 5 seconds an error flashes up and the machine reboots. The error is typically "[7.xxxxxx] not responding" sometimes it comes up as "[5.xxxxxx] not responding". First thing I tried was to boot from the live CD but I also get a variant on the error "[9.xxxxxxxx] not responding" . I think it is a hardware issue but I have no way to capture the boot log to figure it out.  I tried booting in recovery mode to follow the boot sequence but it flashes past the error too quickly. Has any one encountered this, or can anyone tell me how to alter grub to give me a more complete error message?
 
thanks

---

### Post by Lunch2000 on 2010-03-25
Very Weird!
 
Could not boot from HD or Live CD even updated bios and reverted to defaults. Was able to boot live CD version of 9.10. Ran the disk check util and everything was OK messed around a bit mounted the HD poked at some files. Rebooted and HD booted back into 8.10 no problem....

---

### Post by Amof on 2010-03-25
This is a shot in the dark but it kinda sounds like your Hard Drive is failing. I know from experience that Linux will hang up if it is trying to mount a file system that is badly damaged by a dieing Hard Drive. 

I'd run a HDD diagnostic on the computer before you do anything more.

---

