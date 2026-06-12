---
title: "Ubuntu 11.04 not booting"
date: 2011-07-02
forum: General Help
---

### Post by O-pos on 2011-07-02
Hi guys,

I wanted to get rid of ubuntu splash screen, and edited the line GRUB_CMDLINE_LINUX_DEFAULT="quiet
splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet
splash text". Now it won't load at all. It nust shows the same purple background without ubuntu logo, then turns black and shows few lines of text. After displaying "Checking battery state... [OK]", it freezes and does not move further. 

Any ideas?

I can't even.start a recovery mode because I have no dual boot and do not get this opfion at the start. :(

---

### Post by mikejonesey on 2011-07-02
i have multiple distros installed thatway if i break 1 i can fix from another... might be useful for u nehows, if u broke grub, then fix grub from a live cd or create another partition to do this with... :)

---

### Post by O-pos on 2011-07-02
Is there a way to st least start in a recovery mode?

---

### Post by wildmanne39 on 2011-07-02
> **O-pos said:**
> Hi guys,

I wanted to get rid of ubuntu splash screen, and edited the line GRUB_CMDLINE_LINUX_DEFAULT="quiet
splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet
splash text". Now it won't load at all. It nust shows the same purple background without ubuntu logo, then turns black and shows few lines of text. After displaying "Checking battery state... [OK]", it freezes and does not move further. 

Any ideas?

I can't even.start a recovery mode because I have no dual boot and do not get this opfion at the start. :(Hi, you can't just change that line back to the way it was?

---

### Post by O-pos on 2011-07-02
It won't start at all, how can I edit the line?

---

### Post by wildmanne39 on 2011-07-02
> **O-pos said:**
> It won't start at all, how can I edit the line?Hi, I am going  to give you a link it should get you going.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by O-pos on 2011-07-02
All right guys, it's working again.

Following saved me:

First, I went to CLI with ALT+CTRL+F1

Then, I entered sudo dpkg-reconfigure xserver-xorg

Now it is working again. Apparently, it was not a grub issue..

Thanks for your help.

---

### Post by wildmanne39 on 2011-07-02
> **O-pos said:**
> All right guys, it's working again.

Following saved me:

First, I went to CLI with ALT+CTRL+F1

Then, I entered sudo dpkg-reconfigure xserver-xorg

Now it is working again. Apparently, it was not a grub issue..

Thanks for your help.Hi, your welcome would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

