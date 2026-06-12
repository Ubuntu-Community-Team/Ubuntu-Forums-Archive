---
title: "Add/Remove Package Manager freezes"
date: 2010-09-05
forum: General Help
---

### Post by untitledwiz on 2010-09-05
Hello everyone!

I tried installing the Gstreamer plugins but after I gave the package manager my password and the usual small dialog box came up (saying how many files had to be downloaded) the whole application froze. After force quitting it I launched it again and tried to download and install something else but I received an error saying another synaptic was running and I had to wait for it to finish.

I haven't tried using sudo apt-get install because I don't know the exact name of the gstreamer package. In any case, after restarting my computer I tried downloading an arbitrary application and the whole thing froze at the same point. I looked around the forums and the net but couldn't find much.

I run Ubuntu 9.04 (Jaunty) in a dual boot with Mac OS X 10.5 on a Macbook Pro 4,1. I appreciate any and all your help!

-untitledwiz

---

### Post by wilee-nilee on 2010-09-05
If your just trying to get media to work install the restricted extras. In ubuntu it would be in the software center or synaptic: ubuntu restricted extras.

You can also just look in synaptic for the gstreamer your needing.

---

### Post by Jesus_Valdez on 2010-09-05
I thinik that the problem is that Synaptic freezes. 

First try the Terminal way of install, with sudo apt-get install ubuntu-restricted-extras

See if you have any error, you can also launch Synaptic from the Terminal and see what errors gives you, that would be helpful to find out the solution.

---

