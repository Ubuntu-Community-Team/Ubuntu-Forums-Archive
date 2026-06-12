---
title: "Boot hangs when USB KVM switch is connected"
date: 2010-04-14
forum: General Help
---

### Post by greenslime on 2010-04-14
I have been all over the forums looking for a solution to this problem and not found a solution.  

Basically the situation is that the boot hangs if my USB KVM switch is connected.  The keyboard works fine through the KVM switch to access the BIOS menu and in the grub2 menu, but as soon as it starts to boot, I get a black screen with a white cursor on top which never goes anywhere.

The weird part is that if I disconnect the KVM and reboot, it gets past this point and I can reconnect the KVM and both the mouse and keyboard work normally.  However, even if I plug the keyboard in directly but leave the KVM plugged in, the boot hangs.  Something about the fact that the KVM is connected (rather than not detecting keyboard) is causing the boot to stall.

The even weirder part is that this worked fine on my previous build, which was 8.04 upgraded sequentially to 9.10.  But my system drive died so I rebuilt directly from 9.10 ISO and now this does work.  I have tried downgraded to grub .97, I have tried switching between server and generic kernels.

This seems to be the same issue reported in [http://ubuntuforums.org/showpost.php?p=8898301&postcount=3](http://ubuntuforums.org/showpost.php?p=8898301&postcount=3), but it doesn't look like that poster followed up.

I'd appreciate *ANY* ideas on this, because I'm stumped.:confused:

---

### Post by greenslime on 2010-04-14
Follow up... I turned of "quiet splash" and ran update-grub and now see that the boot gets to something like:

"setting up cfq scheduler"

then it hangs.

---

### Post by kvmpro on 2010-04-15
We got some customers reported the same issues of yours in using with KVM switches.  Because the distribution versions of different Linux they all share the similar kernel update - checking and update device status more frequently.   So, those "old" KVM switches providing just  keyboard or mouse emulation can not feed the request from the new OS correctly - which is the main reason the boot procedure hung/stopped. 

We tested UR-12+  and Linux with the new distribution versions and found the switch's built-in  USB DDM (Dynamic Devices Mapping) and its Video Full-time DDC are both providing a very good user experience for all the connected system with the KVM switch. 

I believe the vendor have a special "try-out" program for industry users.

---

### Post by greenslime on 2010-04-29
I finally figured this out, after thinking it was a hardware problem and replacing the USB KVM and STILL having the problem persist, I dug around more and found that adding "pci=noacpi" to the kernel boot parameters allowed me to boot without disconnecting the usb kvm.

The steps for doing this with GRUB2 are a bit convoluted, so I recommend trying it by editing the boot options during boot (esc to get grub menu during boot, e to edit, go to the end of the last line and add "pci=noacpi" (no quotes), then ctrl-x to boot).  If that works, refer to the GRUB2 online docs for making it permenent.

---

### Post by tankzt on 2010-06-01
This didn't work for me.  Any other ideas?

---

