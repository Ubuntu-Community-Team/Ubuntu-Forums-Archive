---
title: "Problem with OpenGL in Ubuntu"
date: 2010-04-04
forum: General Help
---

### Post by maedhros777 on 2010-04-04
Hello, I had recently created a thread on the OpenGL discussion boards about this ([http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=274056#Post274056](http://www.opengl.org/discussion_boards/ubbthreads.php?ubb=showflat&Number=274056#Post274056)). I was told I might have more success on an Ubuntu forum. Near the bottom of the forum, someone recommended trying the AMD driver installer; if someone could explain what AMD is and how to install that would be greatly appreciated, as well as any other help.

---

### Post by cottfcfan on 2010-04-04
Your using an ATI Radeon X300 graphics card.
Try using the proprietary driver from the AMD website.
Search for your card here...

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Read the installer notes 1st and carefully follow the automatic installer instructions.
If you need more info come back.

---

### Post by cottfcfan on 2010-04-04
Just noticed, it looks like AMD have stopped supporting that card.
You`ll probably have to keep using the open source alternative.

---

### Post by clhsharky on 2010-04-04
HI

AMD/ATI still support your ATI Radeon X300 graphics card. It is now supported with OSS Driver 'Open Source Stack' -Radeon, mesa, Xorg-  and not fglrx proprietary drivers on legacy cards.

Even though you have Ubuntu 9.10 stable the drivers are now old for though's who need more OpenGL, 3D or features.

Go here for newer OSS, they are stable in 9.10. 
[https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive)


Sharky

---

### Post by maedhros777 on 2010-04-04
So which package should I download?

---

### Post by maedhros777 on 2010-04-10
Oh, wait, I found the instructions for installing at the middle of the page (using add-apt-repository). So then I updated as it said to, but is the driver now installed? Because I still have the same problem.

---

