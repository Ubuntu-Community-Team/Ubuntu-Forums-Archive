---
title: "Grub menu missing Linux Kernel entries"
date: 2012-07-27
forum: General Help
---

### Post by gilloz on 2012-07-27
From a previous thread, I repaired my grub2 menu, but had multiple entries for my Windows 7, memory test 86+ and Linux Kernels.  I installed Grub Customizer to see if I could eliminate the extra entries and keep only one set.  I screwed up royally.  When I restarted my computer, the Grub Menu only had one each of the Windows 7 loader, memory test 86+ and a memory test 86+ (serial console 115200)  My Linux Kernel entries were missing. Now, I can't boot into Ubuntu.  Short of re-installing Ubuntu, where can I start to fix this?  sigh

---

### Post by drs305 on 2012-07-27
Welcome back *gilloz*.

Assuming (from your previous thread) that the kernels are still there but Grub Customizer isn't letting you see them, try booting from the Grub menu. I'll assume your Ubuntu installation is on sda5 (hd0,5). If it is somewhere else, taylor the commands...

At the Grub menu (hold down SHIFT during boot if you don't see it):

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod linux
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

If you can't load the kernel shortcut above, try the longer version. Since I don't know which kernel you are using, you will have to fill in the correct information. If you have a 'grub' prompt, you should be able to type part of the kernel and initrd.img names and use TAB to complete the name (generic or generic-pae may or may not be part of your kernel name):
```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod linux
linux /boot/vmlinuz-X.X.X-X-generic root=/dev/sda5 ro
initrd /initrd.img-X.X.X-X-generic
boot
```

If it boots, I suggest purging grub, removing all bits of Grub Customizer again (see the GC link for how to do this), then reinstalling GRUB and we can then work on reducing your menu entries.

---

### Post by kc1di on 2012-07-27
> **gilloz said:**
> From a previous thread, I repaired my grub2 menu, but had multiple entries for my Windows 7, memory test 86+ and Linux Kernels.  I installed Grub Customizer to see if I could eliminate the extra entries and keep only one set.  I screwed up royally.  When I restarted my computer, the Grub Menu only had one each of the Windows 7 loader, memory test 86+ and a memory test 86+ (serial console 115200)  My Linux Kernel entries were missing. Now, I can't boot into Ubuntu.  Short of re-installing Ubuntu, where can I start to fix this?  sigh

Hi you may want to try boot-repair also I'd try it first if it works you'll save yourself some time you can get it [here]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by gilloz on 2012-07-27
Thanks guys for your quick responses.  OK, here is where I stand.  My bootloader is on sda1 next to my Windows 7 installation which is on sda2.  When I get my Grub menu at startup, I only have 3 choices.  Windows 7 (loader) (on/dev/sd2), Memory Test(memtest86+) and Memory Test(memtest86+, serial console 115200). Ubuntu kernels are missing from the listing.  I cannot start and boot into Ubuntu, so I have no access to the Terminal.  When I am in the Grub menu at startup, I can get a Command Line which gives me a cursor labeled grub>.  I tried entering Linux and it comes back Kernel not specified.  I tried entering my present kernel, which is Ubuntu,with Linux 3.2.0-27-generic and it comes back with either unknown or not known, I forgot.  In any case, I cannot get Ubuntu started. kc1di, where is this boot-repair located?  I did try a procedure for restoring Grub2 after installation of Windows, and that did nothing for me.  I somehow have to undo what Grub Customizer did.  Thanks

---

### Post by drs305 on 2012-07-27
Click the Boot Repair link in my signature line. You can install and run it from the LiveCD. In addition to the 'Recommended Repair' option, you may need to purge grub from the Advanced option and get rid of any Grub Customizer files as well.

I'm assuming from your post you tried running the commands above from the Grub prompt and were unsuccessful. Since your Ubuntu is on sda1, the commands would use (hd0,1).

---

### Post by gilloz on 2012-07-27
OK.  Here is an update.  I located a Boot Repair for Grub2 at a site called How to Geeks.  I ran through that procedure and I finally got my regular menu back.  I can now access Ubuntu.  This time I do not have many duplicates, but there are a few.  What is the best way to eliminate the duplicate entries?  Don't want to mess with Grub Customizer again.  Drs305, can I just do the sudo apt-get purge grub-customizer to get rid of it and it's files without going through the whole purge procedure?  Kc1di, if that was the boot repair you mentioned, then thanks.

Added: Drs305, your Boot Repair link was the same program that I found in How to Geeks.  I somehow missed your last statement on that.  Thank you also for that.  Now to get rid of those multiple entries.

---

### Post by drs305 on 2012-07-27
By default you should just have one kernel and recovery  mode, a submenu "Previous Linux versions", memtest86+ and your Windows entries.

If you open /etc/default/grub as root, you can remove the recovery mode if you wish by uncommenting (removing the # symbol) from  > #GRUB_DISABLE_RECOVERY="true"
Save the file.

To remove the memtest entries, run:
```
sudo chmod -x /etc/grub.d/memtest86+
```

Run update-grub after making all the changes.

I'm about off to work. If you still have entries you don't want please post your grub.cfg file so we can see what menu items you have and where they are located.

---

### Post by oldfred on 2012-07-27
In addition to drs305's suggestions.

What files are in /etc/grub.d ? 
Some of the procedures on reordering boot menu are copying the scripts like 30_os-prober to some other number earlier in the order like 07_ . But then a reinstall of grub may create duplicate os-prober scripts which creates duplicate entries.

Default scripts:
fred@fred-Precise:/etc/grub.d$ ls
00_header        10_linux      20_memtest86+  40_custom   41_custom
05_debian_theme  20_linux_xen  30_os-prober   40_custom~  README

---

### Post by gilloz on 2012-07-28
There are only two items that need removing from the grub.cfg file.  It is,  Windows 7 (loader) (on/dev/sd2) and "Previous Kernels"  that is it.  Two entries of windows 7 are shown in the .cfg file.  Previous kernels has no other listing below it.

---

### Post by oldfred on 2012-07-28
You often get two Windows entries as a second one is the recovery partition. You can also houseclean out old kernels to remove from list, but most of us suggest keeping two just in case something happens to the one you are using.

Check current kernel I also keep one older just in case:
uname -a
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by gilloz on 2012-07-28
Thanks oldfred for your response.  I am aware of older versions of Linux kernels, but that is not my problem.  I only have 2 lines in my grub menu that I would like to get rid of.  Again, it is one of  the Windows 7 (loader) and Previous Linux Versions.  That's it.  Every thing else is just fine.  All I can find is how to get rid of memory test 86+ and multiple versions of Linux.  Can't find anything on how to get rid of one of two items mentioned above.

---

### Post by oldfred on 2012-07-28
If you delete old kernels you will not have previous versions. 

drs305 has a thread with the ways to edit grub menus, but with grub customizer few want to do it manually anymore.

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I turn off os-prober. I first copy only the entries I want into 40_custom. But I let it update with each new kernel and when that lernel list gets too long, I houseclean. It used to be somewhat easy to modify the script to only find two kernels but I have not tried that with the last couple of versions. You can turn off everything and only have in grub.cfg those entries you want. 

I do something like this for my grub2 installs in flash drives to boot an install or two on my hard drive. 
How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by gilloz on 2012-07-28
Well, I stepped into it again.  I gave up trying to step out of it and it wasn't working.  I just finished doing a complete re-install of Ubuntu 12.04 LTS and I am putting the finishing touches to it.  Thank you all for helping me out.  They should make Grub Customizer more user friendly or bring back the Startup Manager.  For me, it just caused me headaches.  It just wouldn't work for me.  Anyway, I am back to the beginning and enjoying it.  I made copies of both threads for future reference.  Thanks guys.  I appreciate all your help.

---

