---
title: "ubuntu wont start after update"
date: 2010-12-03
forum: General Help
---

### Post by JackRussel on 2010-12-03
I have ubuntu 10.04 lucid with the kde desktop.  While using ubuntu I received a message stating that the system needed to be restarted.  I restarted and when I selected ubunto from the boot menu the computer restarted.  Ubuntu will not load, the computer just keeps restarting.  Everything was working fine until the update asked me to restart the system.  Any one know how to resolve this issue?

I have Windows XP sp3, ubuntu 10.04, 32bit system

---

### Post by oldfred on 2010-12-03
Does XP boot, is this a wubi install?

To see your exact configuration:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by JackRussel on 2010-12-04
I clicked on the following link:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://bootinfoscript.sourceforge.net/")

and then followed the instructions at the bottom in the **Solution** section.  The problem was a corrupted wubildr file located at windows c:/wubildr.  I downloaded the new wubildr file and replaced the old file and then restarted my computer into Ubuntu and everything is now working.  I did notice that the boot sequence took longer than usual.  However, things seem normal inside ubuntu.

---

### Post by oldfred on 2010-12-04
Glad you got it working.

If it is slow perhaps the other fix will help.
Fix for 10.04 upgrade fail bcbc copy wubildr or edit grub.cfg
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

