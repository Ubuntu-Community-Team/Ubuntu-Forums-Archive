---
title: "Too many Boot Menus"
date: 2011-02-21
forum: General Help
---

### Post by catman915 on 2011-02-21
I have a Zotac Mag on which I have installed Windows 7 and  "xbmcfreak-1000-maverick-v2". I use Bootitng as a Multiboot app. When I  installed XBMC it overwrote the MBR and removed Bootit. I Installed Grub  2 to the Root directory of the XBMC installation using a Grub2 boot  disk from Terabyte and reinstalled Bootit. Now everything works fine  with one exception. When the machine is booted up the Bootit menu shows  with the choice of either XBMC or Windows 7. When I pick XBMC it brings  up the Grub boot menu with the choice of either XBMC, XBMC Recover or  Windows 7 in that order. My goal is to have it boot directly into XBMC  when it is selected in the Bootit menu without the Grub Menu showing up  or at least not delaying for the 5 - 10 seconds it does. How would I  edit or change the Grub Menu to accomplish this? I know little or  nothing about Linux and would appreciate any assistance. Thanks

---

### Post by wt8008 on 2011-02-26
You can edit /etc/default/grub, the GRUB_TIMEOUT=10 line to how many seconds you wish the wait before selecting the default kernel.

After editing /etc/default/grub, you need to run sudo update-grub for your changes to take effect on the next boot. 

See [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202) for the meaning of all the variables in the file.

---

### Post by catman915 on 2011-02-26
Thanks

---

