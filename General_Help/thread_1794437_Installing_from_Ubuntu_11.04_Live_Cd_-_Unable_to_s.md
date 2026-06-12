---
title: "Installing from Ubuntu 11.04 Live Cd - Unable to stat the mount point"
date: 2011-07-01
forum: General Help
---

### Post by Tuatar on 2011-07-01
Hi all,

I've installed Ubuntu 11.04 on a desktop and am trying to install ndiswrapper. I don't have a wired connection to the router, but I have managed to use ndiswrapper successfully on other Linux live distributions which already had them installed (eg, Linux Mint 9). 
By inserting the Ubuntu 11.04 Live Cd and adding the cdrom in Synaptic's "Settings > Repositories" menu, I can find it in the list of packages, but when I try to install ndiswrapper-utils-1.9 and ndiswrapper-common I get a few error messages. First, a notice pops up saying:
 "Some of the packages could not be retrieved from the server(s). Do you want to continue, ignoring these packages?". I guessed this is due to lack of an internet connection, so I selected "yes" and got an error box that reads:

"E: Internal Error, No file name for ndiswrapper-utils-1.9

W: Failed to fetch cdrom:[Ubuntu 11.04_Natty Narwhal_-Release i386 (20110427.1)]/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56+r2729-1_i386.deb
Unable to stat the mount point /media/Ubuntu\04011.04\040i386/ - stat (2: No such file or directory)"

This system has two hard drives and a cdrom drive. I've error checked the Live cd, and it came up clean. Please, can someone give me a hand getting Ubuntu to mount the cd?

PS: I've downloaded the ndiswrapper files from sourceforge onto a thumbstick (version 1.56). Is there a way I can install them from  the stick?

Appreciatively,
Tuatar

---

### Post by Tuatar on 2011-07-02
Solved - I've managed to find a workaround solution using the terminal. I managed to install the packages for ndiswrapper from a thumb stick and went from there :)

---

