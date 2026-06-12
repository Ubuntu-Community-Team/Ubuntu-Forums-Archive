---
title: "Removing too many entries from Grub."
date: 2010-08-09
forum: General Help
---

### Post by premjot on 2010-08-09
Hi all,

I use Ubuntu 10.04 and every time I upgrade it there is a new entry in the Grub. I have a list of entries at the startup as I use dual operating systems. Can someone help me with.... so that I can remove multiple entries from the grub and just keep one entry of the ubuntu OS and one for the windows

---

### Post by bergfly on 2010-08-09
This is not intuitive at all, but you need to uninstall the kernels you no longer use and then run update-grub. 

Point 7 on this page covers off what you want to do

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by oldfred on 2010-08-09
drs305 also has another thread on customizing grub2. It has commands you can add to the update scripts to limit the number of kernel entries shown, turn off memtest and other settings.

[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

You can also totally customize:
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by giddyup306 on 2010-08-09
There is also a feature in Ubuntu Tweak to delete old boot options.

---

