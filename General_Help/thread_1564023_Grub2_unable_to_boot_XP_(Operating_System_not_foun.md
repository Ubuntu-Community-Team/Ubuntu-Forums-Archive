---
title: "Grub2 unable to boot XP (Operating System not found)"
date: 2010-08-30
forum: General Help
---

### Post by cmboyd on 2010-08-30
Hi all, I'm new here.

I recently installed Ubuntu Netbook Remix (10.04) on my brother's Acer Aspire One (751h) netbook, set up to dual boot with XP Professional.  The initial install was successful, with both OS's booting correctly.  However, after a series of updates and module builds (this machine has the Poulsbo chipset, still somewhat of a mess), Grub2 is now unable to boot XP, displaying the error "Operating system not found."

To be clear, grub works properly (aside from not booting XP), so the MBR is intact, although I've rerun grub-install to be safe.  Restoring the windows MBR (using testdisk) boots XP happily, but of course ignores the ubuntu installation.  I also had testdisk rebuild the NTFS boot sector, to no change - grub still doesn't work, the windows MBR does.  Using the grub console, I can "root (hd0,1)" and see files on the XP partition, but "chainloader +1; boot" again fails with the same error.  The ubuntu install can likewise mount the NTFS partition with no problems.

Given the fact that switching the MBR fixes the issue, I'm suspecting a Grub2 configuration problem.  However, the simplicity of "root (hd0,1); chainloader +1; boot" leaves me stumped as to what that could be.  Also, the error text "Operating system not found" is suspiciously identical to my BIOS's error message when attempting to boot from a non-bootable medium (as I found out while attempting to make a bootable usb stick with my mac).  If anyone here could point me in the right direction, I'd very much appreciate it.

Thanks,
  Merritt

---

### Post by oldfred on 2010-08-30
If you can boot windows with the windows boot loader in the MBR it does sound like windows is ok. All grub does is bypass the MBR and chainload to the windows boot code in the windows partition boot sector. And that is all the windows boot loader does, it finds the windows active (boot flag) partition and jumps to the boot sector. If it is the same boot sector it should work.

Have you run 
sudo update-grub

To if something looks out of place.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

