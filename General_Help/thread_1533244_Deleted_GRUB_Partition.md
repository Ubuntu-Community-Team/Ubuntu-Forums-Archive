---
title: "Deleted GRUB Partition"
date: 2010-07-17
forum: General Help
---

### Post by jschilli1 on 2010-07-17
Hi, All!

I'm posting today in response to a recent occurance. For the past few hours, I've been trying to remove Ubuntu (I plan on installing it later through WUBI) First, I'd deleted the Ubuntu and GRUB partitions (through the Windows disk manager) I'd restarted, expecting Windows to start. Not so. I got a GRUB error. I went and got my Windows CD(s) and booted from them, hoping to find a Command Prompt window (where I could use the 'bootrec /fixmbr' and 'bootrec /fixboot' commands) An Acer window came up (my manufacturer) but all I got were Windows restore options, so I chose to wipe all of my data and reinstall Windows (I don't really have anything too important on here) That did not work. Same GRUB error when starting up. So I booted from my old Fedora liveCD. Now I'm browsing the web in a search for fixes. No operating systems work at the moment (I can't burn a CD, because Fedora is inside the drive) and I'm kind of in a pickle. If you guys know any way there is to fix this, that's appreciated. I may try to use someone else's PC to burn a liveCD, if needed.

Thanks,

-JS1

---

### Post by wojox on 2010-07-17
Try this [How to Remove Linux and Install Windows XP]("http://support.microsoft.com/kb/314458")

---

### Post by oldfred on 2010-07-17
Do not know if you can do this from fedora or not. Lilo is on many rescueCDs.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

I would download this, just so you have a windows repair cd.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

