---
title: "Virtualbox Help"
date: 2012-01-05
forum: General Help
---

### Post by pcman312 on 2012-01-05
I have a computer that is dual booting Ubuntu 11.10 x64 and Windows 7 32 bit. I want to switch over to Ubuntu full time, but I want to keep windows around using virtualbox. I have created a .vhd file using disk2vhd and saved it on an external usb hard drive (the file is too big to store on either file system at the moment, so I used the external drive). I booted into ubuntu and created a VM in virtualbox using the .vhd file. When I start it, it prompts me with the standard windows "press f12 to select boot device" and then the problem shows up. It prompts with this:
```
error: unknown filesystem.
grub rescue>
```

I've done some googling and found the grub rescue page on the Ubuntu site ([https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)) but nothing I try works. The only command that seems to work is ls and set (though I haven't tried all of them).

I created the .vhd file both with the system resource partition (before C:\ in disk2vhd) and without with the same results.

Is there a way that I can fix this? I don't see grub being needed for this VM since it's a windows only VM, so perhaps some way of removing grub and restoring the windows boot loader? Either that or try to fix grub so that it recognizes the file system.

I do still have the Windows 7 partition and it boots up fine, so I haven't lost any data in case I need to recreate the .vhd file or anything else on windows.

---

### Post by pcman312 on 2012-01-05
I still haven't figured out any solutions to this. I could really use some insight.

---

