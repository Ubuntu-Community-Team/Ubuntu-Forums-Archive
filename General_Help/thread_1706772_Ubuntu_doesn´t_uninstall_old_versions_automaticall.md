---
title: "Ubuntu doesn´t uninstall old versions automatically when updating."
date: 2011-03-14
forum: General Help
---

### Post by in.trouble on 2011-03-14
Hello.

Here is my GRUB boot menu and the older versions of Ubuntu still appear there. It also uses very much disk space.

[IMG]http://i55.tinypic.com/2kql0.jpg[/IMG]

How can i uninstall the old versions and set Ubuntu to do it automatically when i update it?

---

### Post by lithopsian on 2011-03-14
WAD, working as designed.  If you don't want them, uninstall them yourself.  Ubuntu won't do it automatically because each kernel version is a different package.  I suppose they could set the replaces flag in the deb file for every single older kernel version, but you'd be really pissed off if a new kernel didn't work for you and the old one was gone.

---

### Post by Kirboosy on 2011-03-14
_[Ubuntu Tweak]("http://ubuntu-tweak.com/")_ is a handy tool to remove old kernels. I would make sure your computer is perfectly fine and stable before you remove the old kernels. :)


~Caboose

---

### Post by Frogs Hair on 2011-03-14
Ubuntu will not automatically remove old kernel versions. Old kernels can be removed from System > Administration > Synaptic Package Manager.
 
Use the forum search , as there are many threads on this subject and more than one way to go about this task.

---

### Post by scouser73 on 2011-03-14
The best way to remove old kernels would be to install Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Once installed, you'll find it under **System Tools**, select it and it will open up then click on **Package Cleaner** and click on **Unlock** then click on **Clean Kernels** and a list of out-dated kernels will appear and then finally click on **Cleanup**.

---

### Post by lithopsian on 2011-03-14
I don't agree that the best way to remove unnecessary software is to install more software.  There are many ways to remove old kernel versions without installing this tool, either through the GUI package manager or on the command line.

---

### Post by in.trouble on 2011-03-14
Thank you for your answers ;)
I used Synaptic Package Manager to remove them.

---

### Post by Zevaka on 2011-03-14
you can just eventually run ```
sudo apt-get autoremove
```it is supposed (and does very well) uninstall all unused packages.

---

### Post by Foxcow on 2011-03-14
> **Frogs Hair said:**
> Ubuntu will not automatically remove old kernel versions. Old kernels can be removed from System > Administration > Synaptic Package Manager.
 
Use the forum search , as there are many threads on this subject and more than one way to go about this task.





This is the way I prefer to do it as well.  I always search for "linux kernel 2.6.35-xx" and completely remove them.

---

### Post by domu on 2011-03-15
'sudo apt-get autoremove' does not remove old kernels.

But I wrote a command line tool remove-kernel to do this which you can get from 'My Programs' at [http://www.timedicer.co.uk]("http://www.timedicer.co.uk").

Run without options to list installed kernels, or with -h for help.

---

