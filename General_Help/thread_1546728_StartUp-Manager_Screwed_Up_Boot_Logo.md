---
title: "StartUp-Manager Screwed Up Boot Logo"
date: 2010-08-05
forum: General Help
---

### Post by Z3ro3X on 2010-08-05
I was wanting to use StartUp-Manager to increase the resolution of the GRUB menu and the boot logo screen.  Changing the resolution for the GRUB menu works fine.  But the Ubuntu logo that should show up during the boot process is all scrambled across the screen.  I tried multiple resolutions to fix it and none of them work.  How do I restore everything back to their defaults?  I tried putting the numbers all back to where they where when I first ran StartUp-Manager but that didn't fix it.

---

### Post by wilee-nilee on 2010-08-05
Assuming your using grub2 you can edit the default grub file then run update grub.
```
gksudo gedit  /etc/default/grub
```
Look for the screen resolution.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**#GRUB_GFXMODE=640x480**

Then run 
```
sudo update-grub
```

---

### Post by JKyleOKC on 2010-08-05
I had the exact same thing happen to one of my boxes earlier today, and after a few hours of searching the forums (with no luck) happened to stumble across something that solved it for me. Dunno if it will work for you but it's worth a try.

While you're in the editor to change the resolution, look for another line that contains "VGA=771" or something similar. If you find it, delete everything between the quote marks on that line but leave the rest of the line as-is. Then save the file and run "sudo update-grub" to make the changes take effect.

In the original GRUB, VGA codes could be used to establish resolution during the boot process itself. This capability went away with the latest GRUB2, and apparently the presence of the code sent my system into never-never land so far as its fonts were concerned.

I never added the code to /etc/default/grub, and I know it was not there before I started using startup-manager, so I presume that startup-manager itself added it behind the scenes -- possibly as a result of my changes to the boot resolution there!

Hope this helps; we might should file a bug report about it, if you find the same thing has happened to you...

---

### Post by Z3ro3X on 2010-08-05
> **JKyleOKC said:**
> While you're in the editor to change the resolution, look for another line that contains "VGA=771" or something similar. If you find it, delete everything between the quote marks on that line but leave the rest of the line as-is. Then save the file and run "sudo update-grub" to make the changes take effect.

I just solved it moments ago by changing 

GRUB_CMDLINE_LINUX="splash vga=771 quiet"

to

GRUB_CMDLINE_LINUX="splash quiet"

When it boots up I see the Ubuntu logo again.  Log in, check my email and you suggest the same fix, nice. lol  Any way to get the text during boot instead of just the logo?  I'd like to see what's going on behind the scenes as it boots.

On an unrelated note:  I get this before the logo shows up.  Any idea what it means?
/build/buildd/linux-2.6.32/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed

---

### Post by JKyleOKC on 2010-08-05
Yep; take out the "splash" and "quiet" from that same line.

I also like to watch the text flow by. I'm amazed at the time reports it shows in Lucid -- less than 2 seconds here, on a machine that was taking more than 30 seconds to start flowing the text when running Hardy!

I see several similar error messages; I think they are byproducts of making the boot process as universal as possible, since the system does come up and runs properly in spite of them.

EDIT -- I've added my report to bug #495436 in Launchpad, and also to another report of the same bug for which I didn't get the number. The 495436 was first reported in 2009 and still shows as "unassigned" so I seriously doubt that it will get any attention soon!

---

