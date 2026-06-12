---
title: "Unable to modify boot menu in Grub 2"
date: 2009-11-17
forum: General Help
---

### Post by schwim on 2009-11-17
Hi there everyone,

Reading [this page](https://help.ubuntu.com/community/Grub2), it leads me to believe that it uses a smart system for determining the kernels to boot, requiring little to no input from me which is cool.  The only problem is that It's showing all of the old development kernels from when 9.10 was beta.  I'd really like to clean that up.

I found [this page](http://www.ubuntu.com/getubuntu/releasenotes/910)(scroll down to **GRUB menu.lst: install the maintainer's version vs. keep the local version**), which makes me think that I might have chosen to keep the current version of menu.lst.  I thought this wouldn't be much of a big deal, since everyone states that grub no longer uses menu.lst.

How might I go about cleaning up the menu and getting it back to determining the current kernel again?  The last page I linked to shows me how to integrate changes from menu.lst into the boot menu, but I can't find anything that shows me how to get back to automatically determining the boot menu.

Thanks in advance for your time,
json

---

### Post by drs305 on 2009-11-17
Probably the most efficient method would be to remove the development kernels from your system. You can do this from the command line or from Synaptic. 

Once the old kernels are removed, run "sudo update-grub" and the Grub 2 menu will be updated (removing the old kernels from the menu).

I wrote a guide to removing kernel displays from Grub (legacy) a while ago. There is a section on how to remove older kernels that is still current. I wouldn't use SUM but refer to the "Removing Older Kernels" section.

[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")


For making simple/common Grub tweaks (after you have removed the old kernels) such as the default OS/kernel selection, this might help:
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by schwim on 2009-11-17
Hi there and thanks so much for your help.  I removed the older kernel and updated grub and it shows the correct kernel on startup.  I do however have a question:

Do I need to do this every time a new kernel comes down the pike or will simply not choosing to keep the local file of the grub config update it properly?

If I'm thinking about it right, I'll need to remove the kernels manually, then  update grub to get rid of the extra listing, but choosing to update the file will allow the system to use the new kernel.  Is this correct?

Thanks again for your help,
json

---

### Post by drs305 on 2009-11-17
> **schwim said:**
> If I'm thinking about it right, I'll need to remove the kernels manually, then  update grub to get rid of the extra listing, but choosing to update the file will allow the system to use the new kernel.  Is this correct?

Yes, it should work that way unless you have DEFAULT=saved or something other than 0 as your choice. Grub 2 should place the new kernel at the top of the menu, so it would be the new default 0 choice. After removing older kernels running "sudo update-grub" will remove them from the Grub 2 menu.

---

