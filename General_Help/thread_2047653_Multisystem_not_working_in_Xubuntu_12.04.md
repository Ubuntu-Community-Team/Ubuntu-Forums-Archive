---
title: "Multisystem not working in Xubuntu 12.04"
date: 2012-08-25
forum: General Help
---

### Post by cbraxton on 2012-08-25
Multisystem ([http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)) is a great utility for loading multiple bootable operating systems onto a flash drive.

What I'm finding is that on my Xubuntu 12.04 system, Multisystem does not recognize iso files when you try to add them. This happens with both drag & drop or navigating to the iso file, Multisystem just ignores the file and does nothing.

I didn't have this problem on when I was running Ubuntu 10.04 or on other Linux systems I deal with. So far web searches have not turned up any info - anyone here experienced this problem and maybe found a fix for it?

---

### Post by Rexilion on 2012-08-25
I suppose that is an external package you got from ... somewhere... . Furthermore, the educational system tried to teach me French but failed miserably, perhaps an English page somewhere?

Maybe you could start the program from a terminal and see what messages are coming out of it (if any) when you try to drag and drop, might give is a clue.

---

### Post by cbraxton on 2012-08-26
Yes, I should have mentioned that it's not a standard Ubuntu item, have been using it for so long that I sometimes forget that. I'd originally found Multisystem through pendrivelinux.com. I was hoping maybe somebody else here was using it and ran into this problem.

Good idea running it from the command line, should have thought of that myself. I went ahead and did that. The program is really a bash script that runs various other programs to do the heavy lifting. Comments in the script are in French, which unfortunately I don't speak so it's a bit hard to follow what's going on inside it.  In general Multisystem dumps a lot of diagnostics out as it runs, but when attempting to add an iso file it doesn't react at all.

I tried running it via an earlier version of bash taken from Ubuntu 10.04 but that didn't help -- probably an incompatibility with one of the other underlying programs being used to read in the selected file. I'll have to try to work through it, or maybe install a minimal 10.04 virtual machine just for working with my bootable USB drives.

---

### Post by cbraxton on 2012-08-26
Figured it out, Multisystem requires Nautilus in order to be able to open files. I tried installing Nautilus on a hunch this might be the case and it worked. (Probably this is documented on Multisystem's web site but I don't understand French!)

---

