---
title: "blank screen after boot cannot login EVEN IN RECOVERY"
date: 2011-03-11
forum: General Help
---

### Post by arif920629 on 2011-03-11
Hello this is my first thread =D This thing had me wondering for the past 2 hours. I followed this tutorial [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml) to fix the godawful plymouth login screen but i ended up screwing my ubuntu installation (lucid). I can't even login using recovery mode!:confused: mind you i'm using BURG bootloader. Thanks in advance:p

---

### Post by drs305 on 2011-03-11
arif920629,

Welcome to the Ubuntu forums. Please go to this site, download the boot info script, boot to the LiveCD Desktop and run it. Post the contents of RESULTS.txt

This will show us what is happening with your boot files. BURG is close enough to Grub2 that we may be able to help you out, and there are even some regulars who use BURG and may see this thread.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by arif920629 on 2011-03-11
Attached to this post are the results. I ran this on a debian

---

### Post by drs305 on 2011-03-11
When you were running Debian were you booting from the same Grub2/Burg menu and selecting Debian [noparse](sda8)[/noparse] or did you use some other method to get into it? i.e. is it only the Ubuntu menuentries that aren't working when you boot?

Also I am seeing normal Grub nomenclature. I don't know if BURG uses exactly the same file names and folders as Grub2 (such as /boot/grub). Anyway...

If the Grub/Burg menu displays during boot, have you tried to boot manually from the grub prompt? Also, please tell us what happened in Post #1  when you select Ubuntu - error messages, etc.

You can press "c" to get to the prompt, then:
```

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

```
If it doesn't boot, tell us what happens. If you get a failure with the above due to a missing module, you can try adding it:
```
insmod (hd0,5)/boot/grub/<module>  # example: insmod (hd0,5)/boot/grub/linux.mod
```

---

### Post by arif920629 on 2011-03-11
No. I installed Grub2 again to the MBR while running Debian. Maybe that's why BURG does not appear on the result (BURG directory is /boot/burg) and i undid the 'fix' that i did by reverting the etc/default/grub file. When i chose Ubuntu in GRUB it loads but only blank screen when the splash image was supposed to appear. Will try the manual boot immediately :D

---

### Post by drs305 on 2011-03-11
> **arif920629 said:**
> No. I installed Grub2 again to the MBR while running Debian. Maybe that's why BURG does not appear on the result (BURG directory is /boot/burg) and i undid the 'fix' that i did by reverting the etc/default/grub file. When i chose Ubuntu in GRUB it loads but only blank screen when the splash image was supposed to appear. Will try the manual boot immediately :D

When Grub2 fails it is normally accompanied by messages indicating why the boot wasn't successul ("kernel panic", etc). Since you are getting a blank screen, my guess is that the boot is getting past Grub and your problem is with the OS itself.

Are you getting a completely blank screen or do you have a blinking cursor at the top left of the screen. If you have the cursor, it very well could be a video problem (did you try the 'safe graphics' mode in Recovery). You can try to fix a video problem by removing **quiet splash** and adding **nomodeset** to the "linux" line. 

At the Grub menu, press "e" to edit the menuentry, cursor to the end of the "linux" line and make the changes noted above. Press CTRL-x to boot. This change is not permanent. If it boots, go to System, Administration, Additional Drivers/Hardware Drivers and see if there is a video driver available for installation.

---

### Post by arif920629 on 2011-03-11
Hi, sorry for the late reply. For your knowledge i booted to Ubuntu LiveCD and installed GRUB from it. I t cannot detect my Debian installation OMG. Now i'm using Win7 to reply.

Anyways i tried the nomodeset but the same thing happened. No screen. Shouldn't tinker with the GRUB files D=

---

### Post by drs305 on 2011-03-12
> **arif920629 said:**
> Shouldn't tinker with the GRUB files D=

With the lack of error messages I'm still not convinced it's strictly a Grub problem, although it could be one of the kernel options specified in the 'linux' line.

To completely restore default Grub2, you have to purge Grub2 and then reinstall it. Merely reinstalling will only replace missing files that you didn't delete and will not change corrupted files.

If you didn't completely purge Grub2 first, the procedure in the following guide will restore grub to its default settings:


[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

Also, if you are still getting a menu, if you have other kernels available on your system you could try an older one. They have to be on your system but not necessarily in the Grub2 menu. From the G2 menu, press "c", then "ls /boot" and note what kernels are available. Then ESC and "e" the first menuentry. Use the cursors to change the kernel designation in the 'linux' and 'initrd' lines, then CTRL-x to boot.

---

### Post by arif920629 on 2011-03-13
Ok, will try to do it when I have the time.

Note : I already deleted the old kernels from synaptic

---

### Post by arif920629 on 2011-03-13
HEYYYYY I'M TYPING THIS FROM MY MAIN UBUNTU INSTALLATION!!!!!!

I followed your tutorial but i used Debian to use chroot. I purged and reinstalled GRUB and BURG many times but the same thing happened. Then i read the tutorial [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml) again and undid all the changes. After that i did this in chroot :

 [COLOR=#008080]* sudo update-initramfs -u*[/COLOR]

After rebooting i can boot to Ubuntu again!!! Everything's like it was before (even the crappy splash screen lolz) Now if there's a way to disable/change the resolution of that awful splash screen:P Anyways thank you so much for the help. How do i mark this thread as solved? lolz sry imma noob

---

### Post by drs305 on 2011-03-14
> **arif920629 said:**
> How do i mark this thread as solved? lolz sry imma noob

Updating the intitramfs, as you found out, restored your previous kernel image, which is what caused everything to revert.

You can mark it solved via the 'Thread Tools' at the top right of the first post.

---

