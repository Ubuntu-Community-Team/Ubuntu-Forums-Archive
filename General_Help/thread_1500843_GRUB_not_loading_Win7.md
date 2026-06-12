---
title: "GRUB not loading Win7"
date: 2010-06-03
forum: General Help
---

### Post by DJRWolf on 2010-06-03
I updated Ubuntu and part of it was an update to grub. When it came up in the installation I told it to keep the old one and left everything as it was. Then when I tried to reboot into Windows it gave an error message. So I went back into Ubuntu and reinstalled grub and now when I select Windows it just loops back to grub.

---

### Post by oldfred on 2010-06-04
To see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by ryan858 on 2010-06-04
I don't really know about that bootinfoscript... But if you post a copy of /boot/grub/grub.cfg, I can check it out and see if there's anything wrong with it.

If that file doesn't exist, then grub2 never got installed during the updates and it's probably not a bug in grub... But I've seen this issue several times since grub2 came along and it's (so far) always been the cause. And I had a similar problem where Slackware wouldn't show up in the grub menu, because for some reason, grub-update didn't put an ending quote on the menu entry name, and so the rest of the file afterwards was part of the quote. I couldn't even add the OS using the 40_custom file, since it gets parsed into grub.cfg after 30_os-prober, which is where it failed to add an end quote... I didn't figure it out until I disregarded the warning message in grub.cfg and looked in it and added the missing quote. Still, the warning is warranted.. You shouldn't change anything in it unless you know what everything in it does/means (i.e if you know a good bit about shell scripting), and you know what you're doing. If you mess it up you won't even get the option to use Recovery Mode, and you'll have to use a LiveCD to fix it.

If you don't have grub2, then the config file is /boot/grub/menu.lst, and you can post that here...

---

### Post by wilee-nilee on 2010-06-04
> **ryan858 said:**
> I don't really know about that bootinfoscript...

Then you shouldn't be trying to help.;)

---

### Post by oldfred on 2010-06-04
The advantage of the boot info script is it includes many things including probes of the MBR & PBR as well as blkid for UUIDs, all menu.lst or grub.cfg, system files, various windows files like boot.ini and most things we need to see what makes a computer boot and then what may not be correct.

---

