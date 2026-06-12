---
title: "Home folder on Live CD?"
date: 2010-05-01
forum: General Help
---

### Post by Inzuka on 2010-05-01
My linux install will no longer boot, and I am looking to copy an *encrypted* home folder to an external harddrive so I can have all my files when I reinstall Ubuntu.  Does anyone know how I can access those files and put them on the external HDD?

---

### Post by dino99 on 2010-05-01
> **Inzuka said:**
> My linux install will no longer boot, and I am looking to copy an *encrypted* home folder to an external harddrive so I can have all my files when I reinstall Ubuntu.  Does anyone know how I can access those files and put them on the external HDD?

why cant you boot ?

---

### Post by Inzuka on 2010-05-01
[http://ubuntuforums.org/showthread.php?t=1467837](http://ubuntuforums.org/showthread.php?t=1467837)

:P

---

### Post by dino99 on 2010-05-01
> **Inzuka said:**
> [http://ubuntuforums.org/showthread.php?t=1467837](http://ubuntuforums.org/showthread.php?t=1467837)

:P

so you can boot or call a terminal, your problem is with graphics. As you have a nvidia card, like myself, you only need the Lucid packages: nvidia-current, nvidia-current-modaliases, nvidia-settings and nvidia-common

first: sudo rm -f /etc/X11/xorg.conf

---

### Post by Inzuka on 2010-05-01
Forgive me - I'm fairly new to Linux in general.

I can only access a terminal via the Live CD.

Where / what should I be doing with this command?

---

### Post by dino99 on 2010-05-01
follow step by step (adapt with your path) the following thread:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

when done, you can remove xorg.conf (see the command still given) then call synaptic and first remove/purge the previous installed nvidia packages then install the ones i've given into my previous post 

then close  and reboot

note: to see grub menu you have to hold "shift " key down at the end of bios process

---

### Post by Inzuka on 2010-05-01
It's probably the fact that it's 6AM and I'm still trying to fix my 10.04 install, but I'm still confused by what I should be doing.

I'm mounting /dev/sda1, and removing a file?

I'm confused as to why it would be a graphics problem as well, considering I can boot into the Live CD without issues, it's just the install.

---

### Post by Inzuka on 2010-05-01
Hmm... if I am able to reach a plain terminal window while logged on my own home folder (the one I want to copy to the HDD) and I have no GUI at all... is there a command that I can type into said terminal to copy the whole folder to the external HDD?

Also, will I need to mount the HDD from the terminal window before hand?  If so, how would I go about doing so?

Linux is on /dev/sda1 and the HDD is /dev/dbd1.

Thanks in advanced.

---

### Post by wojox on 2010-05-01
Try following this link: [http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

---

### Post by hellomoto on 2010-05-01
> **dino99 said:**
> follow step by step (adapt with your path) the following thread:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

when done, you can remove xorg.conf (see the command still given) then call synaptic and first remove/purge the previous installed nvidia packages then install the ones i've given into my previous post 

then close  and reboot

note: to see grub menu you have to hold "shift " key down at the end of bios process

remove xorg? surly you still need it? I though the nvidia drivers just enabled the hardware, not provided a whole new desktop?

---

### Post by Inzuka on 2010-05-01
> **wojox said:**
> Try following this link: [http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)
I gave this a quick lookover, and it has confused me even more.  I don't have a BackUp of my files, hence why I need to copy my home folder.  :/

---

