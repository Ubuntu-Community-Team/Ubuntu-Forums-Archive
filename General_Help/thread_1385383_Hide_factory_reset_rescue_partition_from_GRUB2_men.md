---
title: "Hide factory reset rescue partition from GRUB2 menu"
date: 2010-01-19
forum: General Help
---

### Post by n411303 on 2010-01-19
I have installed UNR 9.10 Karmic on new Asus EEE pc 1008HA to dual boot with XP. Like many new pc's it has a hidden partition to recover the factory hard disk settings and Microsoft Windows XP. Unfortunately, GRUB2 has picked this up and is showing the recovery system in the boot menu. Clearly this is dangerous because the user could reset the pc. 

How do I remove or hide this boot start up option? Other thoughts: I do not believe Easybcd works with xp/linux. is there another easy bootloader?

---

### Post by tom4everitt on 2010-01-19
Refer to this
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) (more concise)
or this
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) (more pedagogical)
about grub2. 

In short you just need to disable the os-prober. This is done by adding the line:
GRUB_DISABLE_OS_PROBER="true"
to your /etc/default/grub file. 

Then run sudo update-grub. 

This will prevent grub2 from automatically searching for other boot options.

---

### Post by audiomick on 2010-01-19
I think that will also stop it from finding the Windows install proper, which I think the op will want to keep.

æn411303
I am pretty sure you can just remove one entry from the boot menu. Read through the links, that is what I would have to do. If you can find an option to just comment out the reference to the recovery thingy, that might be a good idea. You might need it one day.

---

### Post by drs305 on 2010-01-19
It's not pretty, but you can use the Grub 2 Title Tweaks thread. It includes a way to hide the Recovery partition.

Actually, the menu will look quite nice - it's just you have to go into the 30_os-prober file and edit the script which searches for Windows installs.

Scroll down to Section F.
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

---

### Post by tom4everitt on 2010-01-19
If the windows entry would disappear the solution would be this:

Turn the os-prober back on. 
Run update-grub. 
Find the windows entry in /boot/grub/grub.cfg. 
Copy it and paste it into /etc/grub.d/40_custom (below the current lines). Turn the os-prober off. 
Run update-grub again.

---

### Post by drs305 on 2010-01-19
tom4everette's solution will work, with the disadvantage that Windows and any other OS's not on the system partition won't be found or upgraded. This may or may not be something to consider. For example, if you only have Windows which you won't update, and one Ubuntu install, disabling 30_os-prober wouldn't be much of a sacrifice. 

Another option would be to password-protect the Recovery option. I've written a how-to on that as well. Adding a password to the Recovery option would also prevent anyone other than those designated from editing the Grub 2 menu.  For the time being, the passwords in default Grub 2 are not encrypted, but would provide basic protection from accidental selections and from persons who couldn't access the system files.

[Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019")

---

### Post by drs305 on 2010-01-19
tom4everette's solution will work, with the disadvantage that Windows and any other OS's not on the system partition won't be found or upgraded on future "update-grub" runs (unless made executable again). This may or may not be something to consider. For example, if you only have Windows which you won't update, and one Ubuntu install, disabling 30_os-prober wouldn't be much of a sacrifice. You could also "turn it on" from time to time if you knew an update was available.

Another option would be to password-protect the Recovery option. I've written a how-to on that as well. Adding a password to the Recovery option would also prevent anyone other than those designated from editing the Grub 2 menu.  For the time being, the passwords in default Grub 2 are not encrypted, but would provide basic protection from accidental selections and from persons who couldn't access the system files.

[Grub 2 Password Protection]("http://ubuntuforums.org/showthread.php?t=1369019")

---

### Post by tom4everitt on 2010-01-19
Cool, that would certainly be an option. I didn't know this was possible.

---

