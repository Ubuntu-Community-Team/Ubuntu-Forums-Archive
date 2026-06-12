---
title: "Cannot boot Ubuntu after install win7"
date: 2011-11-29
forum: General Help
---

### Post by fxzf on 2011-11-29
Hello,
 
I have installed the Ubuntu at first and then installed the win 7. However, after I installed the win7, the system always go to win7 straight way without give me and option to choose system. Could anyone please help me sort out this problem? I am using Ubuntu 11.04 32-bits.
 
Thanks very much!
 
Cheers

---

### Post by BC59 on 2011-11-29
You can check on this thread how you can fix it.

[http://ubuntuforums.org/showthread.php?t=1874903](http://ubuntuforums.org/showthread.php?t=1874903)

If you have difficulties here we are.

---

### Post by holycow131415 on 2011-11-29
Basically you need to update grub. You can do this from ubuntu liveCD:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

, or here is another tool as well:

[http://www.webupd8.org/2011/02/live-cd-to-fix-restore-grub-and-grub2.html](http://www.webupd8.org/2011/02/live-cd-to-fix-restore-grub-and-grub2.html)

---

### Post by fxzf on 2011-11-29
> **BC59 said:**
> You can check on this thread how you can fix it.
 
[http://ubuntuforums.org/showthread.php?t=1874903](http://ubuntuforums.org/showthread.php?t=1874903)
 
If you have difficulties here we are.
 
 
Hi
 
Thanks very much for your quick reply!
 
I have used Ubuntu LiveCD to start trail version. And in terminal I have tried.
I have tried sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda. Then, I now can only go to ubuntu. And I also lost internet connection..........
 
Do you think if I can make the windows work and then re-install the Ubuntu without losing any file?

---

### Post by Mark Phelps on 2011-11-29
You need to re-establish boot access to Win7.  To do that, open a terminal in Ubuntu and enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for Win7.

---

### Post by fxzf on 2011-11-29
> **Mark Phelps said:**
> You need to re-establish boot access to Win7. To do that, open a terminal in Ubuntu and enter "sudo update-grub". That will regenerate the GRUB menu and add an entry for Win7.
 
 
Hi 
 
It works!!! Great Thanks for you!

---

