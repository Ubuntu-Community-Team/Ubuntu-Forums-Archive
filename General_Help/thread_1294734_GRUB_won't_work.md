---
title: "GRUB won't work"
date: 2009-10-18
forum: General Help
---

### Post by oh n0es on 2009-10-18
So I just re-installed Windows XP, and lost the GRUB menu that usually loads on boot. I've tried a few different tutorials on getting it back after a Windows installation, and nothing will work.
Any ideas why, or how I can fix it?

---

### Post by ikt on 2009-10-18
If you're using GRUB2 (Ubuntu 9.10 onwards), simply booting into an Ubuntu live cd and running "sudo update-grub" from a terminal should auto-detect the installation and add a menu entry for you.

That is assuming you've installed the windows bootloader over grub on the same drive.

---

### Post by oldfred on 2009-10-18
If it is old grub you still use the liveCD

Quick Re-Install GRUB, if file locations are known
4-step short story

In terminal
  sudo grub
  root (hd0,x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd0)     <-- installs grub IPL to MBR of first hard drive. 
  quit

Reboot

nb: if location of 'stage1' is unknown,
  find grub/stage1
or
  find /boot/grub/stage1
is needed, after step #1

---

### Post by mike555 on 2009-10-18
if you can , download " super grub " and burn .iso as image to cd ...... then boot into it and use it to reinstall grub.

---

### Post by oh n0es on 2009-10-18
> **ikt said:**
> If you're using GRUB2 (Ubuntu 9.10 onwards), simply booting into an Ubuntu live cd and running "sudo update-grub" from a terminal should auto-detect the installation and add a menu entry for you.

That is assuming you've installed the windows bootloader over grub on the same drive.

Nope, I'm running 9.04. If I really need to though, I'll download 9.10.

@oldfred: Already tried that, didn't work, but thanks.

---

### Post by oldfred on 2009-10-18
If a quick reinstall of grub does not work we need to see you entire configuration:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

