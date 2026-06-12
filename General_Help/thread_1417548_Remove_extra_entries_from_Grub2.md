---
title: "Remove extra entries from Grub2?"
date: 2010-02-27
forum: General Help
---

### Post by Tralce on 2010-02-27
I've googled around for answers to this. I have a new Asus laptop which I'm dual-booting Vista and Ubuntu on. When I installed Ubuntu, the recovery partition (/dev/sda1) started showing up in the menu list. I do not want that there because I am afraid of accidentally executing it. 

In the older version of Grub, I recall editing menu.lst How might I go about this now?

I also have extra older kernels listed there which I do not need.

---

### Post by theaaronc on 2010-02-27
This link has a wealth of info on grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


For your issue give these steps a go:


[LIST]
[*]In Synaptic, type the kernel number in the search window at the upper right (for example - 2.6.28-11).
[*]Find the "linux-image" and "linux-headers" files for the applicable kernel (example - linux-image-2.6.26-11 or "linux-image-2.6.26-11-generic).
[*]Right click and select "Mark for Complete Removal" and then press the Apply main menu button.
[*]The kernels will be removed from your system and from the Grub menu.
[*] If you are not sure of the kernel you are currently using, in a terminal type "uname -r".
[*]Many users keep one previous kernel on the machine which previously ran without problems.
[/LIST]

---

### Post by Tralce on 2010-02-27
Thank you sir, and that is a wonderful resource and has answered many of my Grub2-related questions. However, I still am unable to remove the automatically generated Vista recovery partition in /dev/sda1. That guide allows the user to remove automatically added entries for now-removed OSes, but I have not removed that recovery partition. Therefore no amount of editing /etc/grub.d/* allows that one specific entry to be removed. I wouldn't care about it being there, except for the likeliness of in a fit of exhaustion, accidentally booting that partition, which will in turn hose all the files and configs in my existing Vista install. 

The only place I can find in any of the files mentioned in that article that acknowledges that recovery partition's existence is /boot/grub/grub.cfg. It would appear to me that commenting out the entries for /dev/sda1 should solve that problem but I cannot write to that file, even as root.

---

### Post by theaaronc on 2010-02-27
Sorry about that, I misread your original question and thought you were just trying to get rid of Ubuntu related entries.

The reason you can't write to /boot/grub/grub.cfg is because, in order to discourage users from editing it, it defaults to read-only. Running the following command should allow you to edit it with root privileges:

sudo chmod +w /boot/grub/grub.cfg

Commenting out the entry after that should remove it from the grub menu.

Remember that grub.cfg is rewritten and returned to read-only any time the update-grub command is run, which may include system updates done through the update manager. So if you see the windows entry reappear you may have to repeat the process.

I have a dual boot Ubuntu/XP laptop that I may mess around with this on, just for the experience. If I can come up with a better way (not editing grub.cfg) to do this I'll be sure to post a note here. Or maybe some grub guru will come along and square us away :)

---

### Post by Tralce on 2010-02-27
Beautiful. That did work. I was expecting to have to run some other command after editing the file, like with LILO, but fortunately not. Thank you sir.

---

