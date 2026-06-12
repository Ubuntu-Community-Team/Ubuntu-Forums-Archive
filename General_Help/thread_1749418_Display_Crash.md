---
title: "Display Crash"
date: 2011-05-04
forum: General Help
---

### Post by Dookert on 2011-05-04
Hey All

Having a frustrating day. Just got my new HTPC hooked up to my HDTV after installing all the gadgets and programs I like to use. Had everything the way I wanted it, and hooked it up to my TV. Success. Looks great, works like a charm. I decided to run the upgrade manager cause it had about 300 mb up upgrades to go through. Low and behold, upon restart I get about a half second of the ubuntu 10.10 splash screen and then the display goes black. Nothing. I hope somebody can help cause this extremely frustrating. 

As a side note, I had to install the AMD display drivers manually because ubuntu's "install proprietary drivers were too old". Not sure if this would have anything to do with it, it shouldnt right? 



 My computer is a Giada A50 with the AMD fusion chip.

---

### Post by searchfgold6789 on 2011-05-04
You might try adding the 'nomodeset' boot option before Ubuntu boots. Load into the grub menu (it should appear by default but you might need to hold down the shift key to make it appear) and go to the very top option, your Ubuntu OS. Type "e" to edit the boot options, and go down to the line where it says at the end, "quiet splash". After the word "splash" put the word "nomodeset" and press F10. If it works you will have to make the nomodeset option permanent by editing your grub config file later on.
Also, try booting into the Recovery mode using the same GRUB menu. It will give you options like a Root prompt where you can try uninstalling the video driver (which probably has something to do with it), booting into Failsafe Graphics Mode, and other fun stuff.
I hope that one of these two solutions work for you!
 - search

---

### Post by Dookert on 2011-05-04
Fixed it. Ran in recovery mode, reinstalled display drivers, so far so good. What caused it to wig out though I wonder.

---

