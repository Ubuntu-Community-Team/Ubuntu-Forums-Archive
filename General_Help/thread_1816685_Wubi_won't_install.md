---
title: "Wubi won't install"
date: 2011-08-02
forum: General Help
---

### Post by Grunt117 on 2011-08-02
Hello , I am trying to reinstall Ubuntu. I recently installed Ubuntu 11.04 with Wubi just fine but I had to use that partition for something else so I just formatted it. Now I am trying to reinstall it but when I reboot it boots into Windows 7. I checked the all entry's in the windows bootmanger and Ubuntu was not there so I figured that Wubi just didnt add it. I marked the partition that I installed Ubuntu on as active so I can test to see if it really installed. When I booted my computer I got 'BOOT MGR IS MISSING PRESS CONTROL ALT DEL TO RESTART' so fixed it and I went back into Windows and tried to just install it again. Nothing happened just like last time and I am really confused because I have done this many times before. Can some one please help me?

---

### Post by bcbc on 2011-08-02
Wubi doesn't need a partition - it creates a virtual disk. The proper way to uninstall wubi is through the control panel, add/remove programs and selecting the "Ubuntu" entry. 

By formatting the 'drive' with the Ubuntu virtual partition, you removed the uninstall program and left the boot manager entry and also registry entries.

The boot flag is not required for Wubi (or Ubuntu) - it is required for Windows.

So... my suggestion is to try a [manual]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F"), complete uninstall. However, if you have a dedicated partition, why don't you just install direct to it - not with Wubi?

If you still have problems with no bootmanager entry you can add this [manually]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/"), although personally I think it's best to stick to the supported install/uninstall.

---

