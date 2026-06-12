---
title: "Virtualbox error on Lucid"
date: 2010-05-02
forum: General Help
---

### Post by rozbarwinek on 2010-05-02
I have installed Virtualbox 3.1.6 and everything works great until I reboot.
After login when I try to run VirtualBox and NS_ERROR_FAILURE error comes up.
sudo /etc/init.d/vboxdrv setup fix the problem till... next reboot :(
So now I have to recompile VirtualBox kernel module every reboot.
Any idea how to fix it?

---

### Post by BeccaBunny on 2010-05-02
I am having the same issues with mine. If I reinstall it works perfectly but when I load it I get this message 

Failed to Open Create Internal Network.

Failed to attach the Network Lun

Please Install the Virtualbox-ose-dkms package and execute vbox drv as root 

I get error with each one, even following the instructions, but if I reinstall it, it works like a champ!

I have even gone so far as running it as Root using gksu. 

I have a feeling both our problems are related because we are both using Lucid. 

Peace!

Becca

---

### Post by piedro on 2010-05-09
Same here! 

Nobody? 

Seems like you have to reinstall every boot! 

What's wrong? 

plz, help

---

### Post by myjess on 2010-05-09
> **piedro said:**
> Same here! 

Nobody? 

Seems like you have to reinstall every boot! 

What's wrong? 

plz, help
Download version for karmic from SUN/Oracle.

Add yourself to the vbox group in user management.

If still not working, edit vbox menu item and put gksudo in front of command so that it runs as root instead of you.

See if that works.
I have vbox on a couple of 10.04 builds and have no probs with them.

---

### Post by piedro on 2010-05-09
strange! 

there is no group called "vbox". 
maybe this gets deleted every boot? 

too late tonight, will try during the next days ... 

thx, 
piedro

---

### Post by BeccaBunny on 2010-05-11
I also do not have a Vbox group, if I run it as root the issue repeats. 

I will attempt to get it directly from sun and see what happens, and will update with progress. 

Peace Love and Light

Becca

---

### Post by BeccaBunny on 2010-05-14
I uninstalled Virtual Box OSE and then downloaded it from 

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

This is a more closed edition that has USB support among many other things. It Works wonderfully and does not need reinstall on reboot. 


Peace Love and Light 

Becca Bunny

---

### Post by piedro on 2010-05-14
thx becca! 

I immediatly tried this by adding this repository from SUN virtualbox in the sources.lst

"deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free"

Now I found "virtualbox 3.1.8" within synaptic, installed it after removing all the OSE stuff. Since I still had problems I deleted all the kernel modules related to virtualbox. 

(There was a problem with "vboxnetflt.ko" - could not be loaded, so I searched for all the modules "find vbox*.ko" within "/lib/modules" and deleted them all! - yes, backuped before ...) 

Now the beautiful part was: "/etc/init.d/vboxdrv setup" 
Now Virtualbox has rebuild all modules and no more problems ... :) 

Running smooooth ... 

thx for reading, 
cya around, 
piedro

---

