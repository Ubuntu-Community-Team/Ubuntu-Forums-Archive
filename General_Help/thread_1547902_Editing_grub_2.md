---
title: "Editing grub 2 ??"
date: 2010-08-07
forum: General Help
---

### Post by madtom1999 on 2010-08-07
After upgrading to lucid my old laptop X11 stopped working.
After much investigation I found I could get it working by editing the grub 2 menu to add i915.modeset=1 at the end of the line!!
I cannot work out how to make that permanent  - any ideas?

---

### Post by cj.surrusco on 2010-08-07
There is information [here]("http://ubuntuforums.org/showthread.php?t=1195275") about making new entries in Grub 2. 

You would need to copy the original entry from /etc/grub/grub.cfg, paste it into the /etc/grub.d/40_custom file, then add the option that you want. Then update grub using "sudo update-grub".

---

### Post by madtom1999 on 2010-08-07
Back to lilo I think!

Seems (after much guesswork) I need to modify
/etc/default/grub
 entry for GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
and then run update-grub

its gone from tricky to near impenetrable!

---

### Post by oldfred on 2010-08-07
cj.surrusco link is correct but you just need to add to one of these lines and run sudo update-grub.

gksudo gedit /etc/default/grub

# GRUB_CMDLINE_LINUX
If it exists, this line imports any entries to the end of the 'linux' command line (Grub Legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

For the GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE, quotation marks are required (single or double) if the entry is more than one alphanumeric entry. For example, quiet splash requires single or double quotes, while an entry such as quiet would not.

---

