---
title: "How to uninstall a program installed by .sh script"
date: 2011-03-24
forum: General Help
---

### Post by kurtjclark on 2011-03-24
I installed a software on Ubuntu 10.10.  The software came as a .sh file.  Now I want to uninstall it. However I can't find the remove or uninstall script nor can I find the entry of the software in Synaptic.  Is there any uninstall procedure in Ubuntu?

---

### Post by mikewhatever on 2011-03-24
Custom installation scripts may or may not provide removal means, but there is no general rule. Synaptic, obviously, wouldn't know anything about packages that were not installed with apt.

---

### Post by kurtjclark on 2011-03-24
> **mikewhatever said:**
> Custom installation scripts may or may not provide removal means, but there is no general rule. Synaptic, obviously, wouldn't know anything about packages that were not installed with apt.

Would that mean there isn't a way of uninstalling that program except for deleting the folder that the program was installed in?

---

### Post by WorMzy on 2011-03-24
There is an uninstall procedure, but it only works if you installed using the install procedure. You haven't.

The correct way to install software is to search for, and install it from the Synaptic Package Manager (or Ubuntu Software Centre). You can then uninstall this software by marking it for removal in the aforementioned applications.

Since you've used an alternative method of installing software, the uninstall procedure may be very convoluted and confusing, depending on what the shell script you used actually did.

Open the shell script in gedit (or your preferred text editor), and copy and paste it's content here (**put [CODE] tags around it, please.**). Alternatively, post a link to the exact webpage you downloaded the script from.

---

### Post by mikewhatever on 2011-03-24
Well, removing installed packages manually (rm) is always an option, however tedious and uninspiring.

---

### Post by beew on 2011-03-24
I have installed a few things like that. Usually they are installed in the home folder or /usr/local/ basically just delete the folders and that's it. Never had a problem. If you want to be thorough you can make a search then delete. It is actually simpler than in Windows (no registry to worry about)

---

### Post by kurtjclark on 2011-03-24
> **WorMzy said:**
>  tags around it, please.**). Alternatively, post a link to the exact webpage you downloaded the script from.
The .sh file is about 500Mb odd in size and when trying to open it with gedit it says gedit is unable to detect the character encoding of the file.

---

### Post by WorMzy on 2011-03-24
Blimey. Are you sure it's a .sh script, and not a .run file?

It's probably best if you post a link to it instead.

---

### Post by beew on 2011-03-24
> **WorMzy said:**
> 
The correct way to install software is to search for, and install it from the Synaptic Package Manager (or Ubuntu Software Centre). You can then uninstall this software by marking it for removal in the aforementioned applications.



Provided the software is in the repository. But people do use softwares that are outside of the Ubuntu system, for example, paid softwares.

---

### Post by beew on 2011-03-24
> **kurtjclark said:**
> The .sh file is about 500Mb odd in size and when trying to open it with gedit it says gedit is unable to detect the character encoding of the file.

You can choose the decoding option. But it doesn't matter, just search for the installed folders (if you don't know where they are already) and delete them. You don't need uninstalling. You need that in Windows because of the registry (**Edited:** Third party softwares installed this way don't have their pieces scattered in various directories and being used by other programs like those installed via apt-get, so it is ok to simply delete)

---

### Post by kurtjclark on 2011-03-24
> **beew said:**
> You can choose the decoding option. But it doesn't matter, just search for the installed folders (if you don't know where they are already) and delete them. You don't need uninstalling. You need that in Windows because of the registry (**Edited:** Third party softwares installed this way don't have their pieces scattered in various directories and being used by other programs like those installed via apt-get, so it is ok to simply delete)


Ok! Thanks for all the suggestions.
Here's what I did I ran the .sh file again and it ran the installer for the software.
Then at some stage it asked me that the software has already been installed and it would need to be uninstalled if I wanted to install it again so I selected yes and it did some uninstalling operation. Then I manually deleted the installation folders.
I guess that was the best that I could do.

Thanks again.

---

