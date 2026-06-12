---
title: "really simple questions - need simple help."
date: 2009-10-27
forum: General Help
---

### Post by watchman323 on 2009-10-27
Before I make a bad video driver installation, what and where is the file that I need to make a back up at?  Now after I made the bad video driver installation and gets a black screen, what do I do next?  Can I go back to my default stable video driver, if so, how?  Do I go the prompt and goto the directory where the file is located then copy the backup that made to the new one.  Will that change my video back to default?
Could someone please show me the scripts or commands for the things I mentioned here.  I am still new to Ubuntu.  I enjoyed the days of DOS 3 and 5, not a fan of 4.

---

### Post by fancypiper on 2009-10-27
The file is /etc/X11/xorg.conf and after an install, I like to copy that file to /etc/X11/orig.xorg.conf

In my upgrade file (/etc/X11/xorg.conf.dist-upgrade-200910241645), they have a comment:

# If you have edited this file but would like it to be automatically updated 
# again, run the following command: 
#   sudo dpkg-reconfigure -phigh xserver-xorg

That command might be worth a try.

---

### Post by watchman323 on 2009-10-27
What happens if my system can't boot up to gui screen?  I type cd /etc/X11 then copy my old (default) file to the installed one - is this right?  Then I should be able to boot back to my gui again?

---

### Post by fancypiper on 2009-10-27
Yes, but you need to do it as root

---

### Post by watchman323 on 2009-10-27
Is this the command I use? 

$ cp /etc/X11/old.xorg.conf /etc/X11/xorg.conf


Sorry for this kind of details.

---

