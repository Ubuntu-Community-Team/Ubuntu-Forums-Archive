---
title: "Dual-Booting question."
date: 2009-07-24
forum: General Help
---

### Post by DrCuddles on 2009-07-24
I have been dual booting Windows 7 and Ubuntu 9.04 on my laptop for as long as 9.04 has been out because I need the low memory usage that Ubuntu gives with some very hungry programs, anyway my reason for dual booting doesn't matter lol, I just wanted to ask if it was possible to do something which I guess it is but I don't know how.

When I boot my laptop up it instantly loads up GRUB and goes to boot into Ubuntu, but I use Windows much, much more than Ubuntu and so would like it to bypass GRUB and go into the windows boot loader (which has windows selected automatically and Ubuntu as the secondary option).

Any ideas?

---

### Post by oldfred on 2009-07-25
If you want to keep GRUB in the MBR you can edit menu.lst to move the windows boot above the ubuntu's and change the timeout to 3 seconds just in case you want ubuntu from GRUB.

Move the windows stanza lines title, boot etc 
to here
## ## End Default Options ##
   ubuntu kernals boot stanzas here
### END DEBIAN AUTOMAGIC KERNELS LIST
windows lines that were here, move above.

When Ubuntu updates kernals everthing in between the above lines is rewritten with the new versions, so do not put anything in with the ubuntu lines. Before or after is ok, but many of the commented lines at the top are used to help write the new line for a new kernal.

---

