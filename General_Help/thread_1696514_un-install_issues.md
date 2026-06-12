---
title: "un-install issues"
date: 2011-02-27
forum: General Help
---

### Post by red40y on 2011-02-27
I uninstalled wubi from my laptop, but there is still an potion to load ubuntu on start up. i uninstalled ubuntu  properly and deleted all residual files from the computer. i also tried using a hdd partition utility to get rid of the grub. how do i get rid of the ubuntu option on start up for good?

---

### Post by Rubi1200 on 2011-02-27
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

Depending on which version of Windows you have, you can follow the instructions in the link above to edit the boot.ini file.

---

### Post by red40y on 2011-02-27
currently running win7, ill give it a shot and report back.

---

### Post by DanneStrat on 2011-02-27
> **red40y said:**
> I uninstalled wubi from my laptop, but there is still an potion to load ubuntu on start up. i uninstalled ubuntu  properly and deleted all residual files from the computer. i also tried using a hdd partition utility to get rid of the grub. how do i get rid of the ubuntu option on start up for good?

Hi.

The wubi installer adds an entry to ubuntu in the "boot.ini" file

and it seems like the uninstaller failed to remove it.

I don't know which windows windows version you're using

so I will give you the procedure for xp ,vista and 7.

You can remove it by doing the following:

[B]
If you're using xp:

[/B]Edit the "C:\boot.ini" file and delete the Ubuntu/Wubi line.

Here is how to do it:

[http://support.microsoft.com/kb/289022/en-us](http://support.microsoft.com/kb/289022/en-us)


[B]If you're using vista or 7:

[/B]Use easybcd to remove the "ubuntu entry"

You can download it here:

[http://neosmart.net/downloads/software/EasyBCD/EasyBCD%202.0.2.exe](http://neosmart.net/downloads/software/EasyBCD/EasyBCD%202.0.2.exe)

---

### Post by red40y on 2011-02-27
i tried using easybcd but the only entry that came up was win7. no change was made on reboot
i also tried the method from the wubi wiki with no success. this is right now, i have it set up to have no wait period when choosing what i want to boot so it go to win7 after 1 sec. but its not the fix i was hoping for. i was under the impression that installing ubuntu with wubi, you can uninstall just as easily through the windows control panel. why is this not the case?

---

### Post by Rubi1200 on 2011-02-27
Perhaps try restoring the Windows bootloader?
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I have heard of this happening before, but usually editing boot.ini or using EasyBCD fixes the problem so I am not sure what is going on in your situation.

---

