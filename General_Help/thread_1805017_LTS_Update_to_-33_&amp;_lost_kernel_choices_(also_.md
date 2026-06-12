---
title: "LTS: Update to -33 &amp; lost kernel choices (also: 32bit compatibility)"
date: 2011-07-15
forum: General Help
---

### Post by Vakkotaur on 2011-07-15
I've updated my LTS Xubuntu install to the recommended -33 and on boot I no longer have the selection of kernels to boot into.  This by itself would pose no problem except that I've also run into a problem with the 32-bit compatibility.

For -28 and earlier, I could run Second Life clients (Phoenix, Firestorm, etc) that are 32-bit without significant issue.  Everything after -28 fails when I try it, giving me an error like:

The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 16 error_code 1 request_code 156 minor_code 19)

Searching Google, I find this means that the program is looking for 32-bit libraries in the wrong place. But since the program has not changed, the libraries have not moved, and booting into -28 has everything still working, there must be rather more to it than that.

I have tried 'update-grub' and it listed the various kernels it should have as options.  When I reboot (I've tried more times than I care to think about) I don't get any options, just a direct launch into the Xfce login.  I do not recall setting an option for this behavior, assuming there is one.

How do I get my boot choices back?

How can I get 32 programs to run as expected with a recent kernel version?

System is an AMD Phenom II X6 w/16GB PC1600 on Gigabyte GA-890XA-UD3 motherboard & ATI Radeon HD 3870. No overclocking.

---

### Post by ajgreeny on 2011-07-15
I assume you mean that you do not see the grub menu when you boot the machine.  If this is correct, simply hold shift key just after the POST at boot, when you would expect to see grub, and the menu should appear.  The default is for the grub menu to be hidden if you only have a single OS on the machine, which is your situation, I imagine.

You can always see what the menu will contain, when it shows, with the command ```
grep menuentry /boot/grub/grub.cfg
```which is much easier than searching the whole of grub.cfg

---

### Post by Vakkotaur on 2011-07-15
That's exactly it, though why should that manifest just now? With all previous (even the initial install) I had the option shown to me.  This is a sudden, unexpected change of behavior.  I would go so far as to call it a bug due to violation of the Principle of Least Surprise.

---

### Post by ajgreeny on 2011-07-16
> **Vakkotaur said:**
> That's exactly it, though why should that manifest just now? With all previous (even the initial install) I had the option shown to me.  This is a sudden, unexpected change of behavior.  I would go so far as to call it a bug due to violation of the Principle of Least Surprise.
I do not know why you saw the grub menu previously if you only had a single install of Xubuntu on the machine, as the default is to hide grub when there is only a single OS available, on the grounds that:-

1.  there is no point offering a choice if there is no choice to offer, and 

2.  the menu can always be forced to show by pressing shift if you need to choose the kernel to boot.

Have you removed a second OS at any time?  That might explain things.

Unfortunately I can not give you any help with your 32 bit compatibility problem.

---

### Post by Vakkotaur on 2011-07-16
I recall at initial install and each upgrade thereafter until now that there was a choice, even with just the one kernel there was a choice of the standard kernel and a fallback as a safe mode.  I don't know for sure if this was actually a different kernel in some way or simply something with commonly problematic options switched off.

I was about to say that the machine was always single-OS, then realized that while it was only single-boot that an older IDE drive with PCLinuxOS has been removed.  I could not boot that, but it was there. That might have been an issue except to pull the drive I had to shut down - and I still had the choices presented after that.

As for point 1, it is quite clear that there are choices to offer, between the kernel versions. Removing options/choice (or hiding them) seems a very Gmone-ish/Windows-ish thing to do.  Is there a way to get grub2 to always present the choices, short of installing another OS?

Granted, I do plan to install another OS (PCLinuxOS again when there is a 64-bit version available) but see no point in doing for something that should be a trivial tweak.


As for point 2, oh well.  Having dropped back to -28 it confirmed a suspicion I had: -33 messed up video.  I still got video, but the simple act of dragging a Terminal window across the screen resulted in odd jitters and slow trail-leaving redraws.  Naturally I do not consider that to be an upgrade.

---

### Post by Blasphemist on 2011-07-16
There is an easy to use customizer that can be used to change the timeout from 0 to whatever you want. Please see grub customizer and more in the footer of the op from this post. [http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I believe it also has a setting on whether or not to give you an option for the old kernels. I don't know the solution to your 32 bit issue but if you report that issue as a bug with information in detail of the programs, kernels and what you know about the libraries someone may be able to solve it.

---

### Post by ajgreeny on 2011-07-18
> **Vakkotaur said:**
> I was about to say that the machine was always single-OS, then realized that while it was only single-boot that an older IDE drive with PCLinuxOS has been removed.  I could not boot that, but it was there. That might have been an issue except to pull the drive I had to shut down - and I still had the choices presented after that.
That is therefore why you saw the grub menu.  Even though that OS would not boot, for whatever reason, it was still present, and therefore would have been found by grub, and forced the menu to show at boot.

Having subsequently removed the PCLinuxOS disk, and now having run update-grub, which happens when a new kernel is added by updates, the default will have changed to hide the menu again.

Had you removed the disk with PCLinuxOS from the machine before  installing Ubuntu, you would then have had a single OS machine and the  grub menu would have been hidden from the start.

---

