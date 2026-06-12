---
title: "Using the extra buttons on the eeepc?"
date: 2010-02-15
forum: General Help
---

### Post by jeff.sadowski on 2010-02-15
What is the correct way to go about this?

I have my own solution since the extra keys that are not mapped already show up as acpi events.

I know of a program called kbde that acts as a keyboard input.
I was going to add an event for each unmapped key and have it use kbde to type a visible keycode that I can use to run whatever I want. kbde has a few keycodes that are not used by any keys I have; I could just use those.

here is how to use kbde
> 
sudo apt-get install cvs
cvs -d:pserver:anonymous@kbde.cvs.sourceforge.net:/cvsroot/kbde login
cvs -z3 -d:pserver:anonymous@kbde.cvs.sourceforge.net:/cvsroot/kbde co -P 
cd kbde/kbde-driver;make
sudo cp driver/kbde.ko /lib/modules/`uname -r`/misc
sudo depmod -a
sudo mknod /dev/kbde c 11 0
cd ../kbde
make
sudo cp utils/kbde /usr/bin


kbde -l to list keys it can output

I forget how to use ACPI events but I can figure it out in a few minutes.


will keytouch work?
or is there some program like kbde that can output a keycode?

Where do I put module code I want to have it try to compile each time I install a new kernel?

---

