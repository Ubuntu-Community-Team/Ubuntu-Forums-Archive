---
title: "Dual boot Ubuntu, fails to login"
date: 2006-06-27
forum: General Help
---

### Post by barnesdmd on 2006-06-27
I've just started running Ubuntu on Dual boot with Windows XP on a seperate NTFS partition using an IBM x21 laptop. Grub appears to be working fine however when proceeding to boot Ubuntu the error:

"hub 1-1:1.0: Cannot enable port 1. Maybe the USB cable is bad?" 

appears at several points before Ubuntu loads. I'm unsure being new to Ubuntu whether this is relevant or not but after entering username and password I have failed to get any further, the initial center box appears however no modules load within it. I receive the same error repeatedly when shutting down from here as well which carrys on until a hard reset is performed. 

Has anyone any ideas as to what this could be? Are the two issues related?

Many thanks in advance!

---

### Post by zxee on 2006-06-28
Don't know if that error message is relevent to your inability to boot into ubuntu, but I think it's worth a shot to stick in the install/live cd and type linux rescue <enter> at the prompt.

---

### Post by barnesdmd on 2006-06-28
do you mean the boot options prompt or the terminal within ubuntu live? I've tried both without success so far...

Since posting last night I've discovered a couple of other things, the USB fault seems to be related to the laptops docking station as it doesn't happen upon removal. I attempted to re-install ubuntu last night which appeared to go more or less successfully. However upon reboot ubuntu starts to load and stops on 'Waiting for Filesystem', this happens both in recovery mode and on the standard boot. At a bit of a loss as to what to do now!

---

