---
title: "How does Karmic set text console screen resolution?"
date: 2010-01-21
forum: General Help
---

### Post by flabdablet on 2010-01-21
I'm trying to track down a screen resolution issue (Karmic on an Acer SK20 [Intel 945 graphics] with Acer AL1511 flat panel via VGA) and I'd appreciate somebody explaining the mechanism for setting the framebuffer screen resolution after GRUB2 has loaded the kernel but before X starts.

Before I forced it to behave itself by adding an xorg.conf with a lone "Modes" entry for 1024x768, X was setting the panel to 640x350 by default. It appears from looking at get-edid | parse-edid that this is because 640x350 is the only resolution this idiot panel's EDID says it knows about, even though its native resolution is in fact 1024x768.

So the GUI works fine now, but all the text consoles (Ctrl-Alt-F1 through F6) are still operating at 640x350 and look terrible; also, because usplash doesn't know what to do with 640x350, I don't get my nice white Ubuntu logo before GDM starts.

In previous releases, I would have dealt with something like this by adding vga=791 to the kernel boot options. That doesn't work for the Karmic kernel, and GRUB2 whines about it being deprecated and tells me to use "set gfxpayload=1024x768x16,1024x768" on a line before the "linux" command instead.

Things I have already tried, with no success:

1. Adding "set gfxpayload=1024x768x16,1024x768" into the boot sequence, right before the "linux" line, by using GRUB2's inbuilt boot sequence editor (Ctrl-E): no change.

2. Changing the GRUB_GFXMODE= line in /etc/default/grub and running update-grub: changes the resolution used for GRUB's own menu, but as soon as the kernel boots it's back to 640x350 on text consoles.

3. Same as (2) but also adding a "set gfxpayload=keep" line in /etc/grub.d/00_header, right after the "set gfxmode=${GRUB_GFXMODE}" line: same effect as (2).

4. Removing the "splash" option from the "linux" line. No change (I guess this is because usplash didn't work anyway at 640x350). By the way, usplash.conf is set up for 1024x768 and yes, I did remember to dpkg-reconfigure -phigh usplash to rebuild the initramfs after checking this.

So my question is: where exactly does Karmic set the screen resolution for its text consoles, and how can I force it to ignore this LCD panel's bogus EDID?

---

### Post by dcstar on 2010-01-21
> **flabdablet said:**
> 
.........
So my question is: where exactly does Karmic set the screen resolution for its text consoles, and how can I force it to ignore this LCD panel's bogus EDID?

Have a look at this:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by flabdablet on 2010-01-21
OK, I had a look at that, and it looks like the method it uses for controlling the resolution I want to control is inserting vga=xxx boot options into the Grub configuration file, which I've already done by hand and which appears to have no effect at all on the Karmic kernel, merely prompting whining from Grub2. But I'll give it a whirl anyway, just in case it knows something I don't.

---

### Post by flabdablet on 2010-01-21
Huh. it looks like vga= is in fact the correct method but is just not working right now.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/391215](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/391215)

---

