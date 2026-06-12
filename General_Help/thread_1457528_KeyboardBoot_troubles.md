---
title: "Keyboard/Boot troubles"
date: 2010-04-18
forum: General Help
---

### Post by Sibbly on 2010-04-18
I'm not sure this is the correct plasce to post this but I have a serious problem. I installed Ubuntu on my computer but it caused it to become run much worse. I would have just gone back to the windows operating system, but my keyboard doesn't work while my computer is booting so I can't change my operating system. I changed it to Ubuntu while in Windows. I edited the grub file because that's what all the help topics said to do. When I did this it made my computer have an error when starting. It then says press any key to continue. I can't press any key because my keyboard doesn't work during boot. I am now stuck and can't ever get past start-up. What can I do?

---

### Post by Kai Summers on 2010-04-18
Download and write a live cd of the Ubuntu Distro and redo the installation off the installation cd not via windows. That way the installer will do all the work for you, creating the GRUB entries manually for any dual boots etc.

---

### Post by oldfred on 2010-04-18
Check your BIOS settings for USB keyboard or PS/2 keyboard. 

I had this problem a year ago and my work around until I found the BIOS setting was to use a USB to PS/adapter and switch just during booting. Some systems ignored the BIOS settings and worked, grub now uses the BIOS setting.

---

