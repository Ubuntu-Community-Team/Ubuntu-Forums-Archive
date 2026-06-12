---
title: "How to have less boot options?"
date: 2010-04-02
forum: General Help
---

### Post by diego_pmc on 2010-04-02
I have both Ubuntu and Windows XP installed on this computer. This isn't that big of a problem, but I would like to know if there's any way to remove the other four or so boot options for Ubuntu and leave only the 'standard' boot options for Ubuntu and Windows XP. I am new to Linux so I doubt I'll be using those any time soon so I'd like to have them out of my way for the time being. :)

---

### Post by Elfy on 2010-04-02
You can do that with startup manager

[http://ubuntuforums.org/showpost.php?p=5112620&postcount=1](http://ubuntuforums.org/showpost.php?p=5112620&postcount=1)

---

### Post by revenant138 on 2010-04-02
you can also edit /boot/grub/menu.lst, though that just takes them off the list.

---

### Post by eksasol on 2010-04-02
Grub2 is a different file now, its at **/boot/grub/grub.cfg**
First you have to chmod grub.cfg to give yourself permission to save changes to the file. Delete entries you need, then lock the permission when you're done. 

I know for the original Grub there was KGrubEditor, but it doesn't work with Grub2.

---

### Post by Elfy on 2010-04-02
> **eksasol said:**
> Grub2 is a different file now, its at **/boot/grub/grub.cfg**
First you have to chmod grub.cfg to give yourself permission to save changes to the file. Delete entries you need, then lock the permission when you're done. 

I know for the original Grub there was KGrubEditor, but it doesn't work with Grub2.

If you do this then as soon as grub gets an update all changes will be lost - changes to grub2 need to be made to other files and then update-grub run.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by diego_pmc on 2010-04-02
I installed Startup Manager but I don't know where the to find the option to remove/hide boot options.

---

### Post by oldfred on 2010-04-02
Startup manager with grub2 is more limited as grub2 is new.

More info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by diego_pmc on 2010-04-02
Thank you for the help.
Hey, Linux ain't that bad! :D

---

