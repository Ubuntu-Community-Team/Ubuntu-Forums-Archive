---
title: "How do I edit the grub.cfg file?"
date: 2010-10-04
forum: General Help
---

### Post by gilloz on 2010-10-04
Since I updated my 10.04 LTS program from 2.6.32-24 to 2.6.32-25, both of these show up at the dual boot start up menu.  Back when I had 8.04 LTS, I was able to edit my menu.lst file to delete past versions.  How do I remove past versions from the grub.cfg file at present?

---

### Post by Rubi1200 on 2010-10-04
You don't edit grub.cfg directly.

To remove older kernels from the GRUB menu search in Synaptic for linux-image and linux-headers for the kernel number and remove those files (there will be 3 in total).

However, it is advisable to always keep at least one spare kernel so that in the event an upgrade/update goes wrong you can always boot into an earlier version.

For more about GRUB2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Soul-Sing on 2010-10-04
as said by rubi1200

or/and/maybe via /etc/default/grub

(and [COLOR="Red"]startupmanager[/COLOR] could play an important role in managing grub2 as well)

---

### Post by gilloz on 2010-10-04
Thanks guys for your responses.  Actually, I only want to remove it from the start menu only so it doesn't start to show all of the updates.  Only keep it or show the current one.  I thought that removing only the text from the start menu was by editing the grub.cfg file.

---

### Post by efflandt on 2010-10-04
If you edit grub.cfg just be aware that it will be rewritten any time there is a kernel update or anything else runs update-grub, based on what is in /etc/default/grub and scripts in /etc/grub.d/.  So /etc/default/grub or /etc/grub.d/ scripts is where you normally configure how you want grub.cfg to appear, but you would have to know what you are doing to exclude specific kernels (short of simply uninstalling those kernel versions from your system as explained by Rubi1200).

---

### Post by oldfred on 2010-10-04
If you want to customize this has lots of useful info:

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by philinux on 2010-10-04
I tend to use this.
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by garner_nc on 2010-10-04
I edit my grub.cfg. When I'm done I make a copy (grub.cfg.bak) and keep it in the same directory. When I get a kernel upgrade and grub overwrites the existing file. I just copy over my backup and manually add in the new kernel entry.

Easy. The way it should be. The way it was.

Sitting here on my desk I have instructions for upgrading from Grub 2 to Grub Legacy. I say upgrade because this would be an IMPROVEMENT. 


All the Best,
D. White

---

### Post by oldfred on 2010-10-04
the better way is to just copy anything you want into 40_custom and edit at will. You can turn off osprober and other updates.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by gilloz on 2010-10-05
Thank you all for your responses.  It seems I have found my solution in reading the responses with regards to Grub 2 links.  Using a program called Ubuntu-Tweak appears to do what I was asking in removing previous Kernels from the start-up menu.  Although I only have one previous Kernel, they all suggest to keep one older one as a possible backup, for now.  Thanks for all the links and information from all of you.  I have printed this Thread for future use.  I really appreciate this.

---

