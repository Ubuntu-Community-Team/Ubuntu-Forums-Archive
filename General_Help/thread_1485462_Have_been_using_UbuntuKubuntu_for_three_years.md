---
title: "Have been using Ubuntu/Kubuntu for three years"
date: 2010-05-16
forum: General Help
---

### Post by gabmuks on 2010-05-16
Today my computer would not boot. The boot would start ok when powered up computer,
but would not finish booting. Boot stops midway, screen goes black. But computer stays
powered up. So far have tried removing small battery for two minutes and then
replacing. Have removed both memory cards and then replaced them.
I have reinstalled Kubuntu 10.4 four times. Nothing has helped so far. Nothing has made any improvement. But also it hasn't gotten any worse.
The last thing that I did before this booting problem started, was download a "Date and Time" widget from a website that I found in the "Add/Remove programs" list.

I found something on the net that says I could have a BIOS boot virus.
Would it help if I flashed the BIOS?

Any help would be appreciated. I can still use the computer after a clean install, as long as I don't shut it down. Because it will not reboot.

Regards

Pat L.

---

### Post by Zorael on 2010-05-17
The thread title isn't very descriptive of the topic. :3

This could either be the boot process stalling, the computer freezing, or X failing to load properly.

If you disable the boot splash, you should instead be presented with a textual boot detailing what's actually happening. In the GRUB2 bootloader menu, select your kernel entry and hit Ctrl+E (or perhaps just E?), then scroll down to the **linux** line, and remove '**splash**' near the end of it. Hit Ctrl+X to execute and start the boot process. To get an even more verbose output, remove '**quiet**', too.

As for X failing to load, you would need to refer to **/var/log/Xorg.0.log** and **/var/log/kdm.log** to see if they list any errors. You could do this from a live cd/usb session.

---

### Post by gabmuks on 2010-05-20
Thank you very much for information. I see now that it is important to learn
about the Linux language.
Up until now I have got by with "copy and paste" into a terminal.

But I guess that wont solve my booting problem.

What is best way for me to learn what a "kernel" is?

And how to properly use Linux commands?

Thank you for your kind reply.

Pat L.

---

### Post by Peter09 on 2010-05-20
What version of Ubuntu are you using. You should be able to get to the recovery mode by holding the shift key down while it boots (Lucid) or hitting escape. 

When you get to the grub menu use the arrow keys to drop down a line to the recovery mode and hit enetr.

Try selecting the graphics option in the menu.

---

### Post by Peter09 on 2010-05-20
I would suspect that you have a disk error. You could try booting using the LiveCD and the checking the disk using fsck. Depends how confident you feel.

---

