---
title: "Changing the color of startup text"
date: 2009-10-23
forum: General Help
---

### Post by Jaraxle on 2009-10-23
Hello all,

I am trying to increase the resolution of startup text (after Grub and before login) and also set the color of the text to green, like in some distro's.

I followed the guide located here:

[http://ubuntuforums.org/showthread.php?t=50054](http://ubuntuforums.org/showthread.php?t=50054)

and was able to change the resolution by adding =792 to my default boot option. I was also able to edit /lib/lsb/init-functions and locate the log_end_msg () function referenced in the guide.

I added GREEN=`$TPUT setaf 2` as indicated but clearly this file has changed in Jaunty. (The guide is actually from 2005). I was unable to find the function to add the second ${GREEN}ok${NORMAL} command.

I went ahead and saved changes (after first creating a backup), rebooted, and, alas, no green text. Could anyone guide me through this for Jaunty? Or does anyone know of another way to do this? Again, I'm just trying to change startup text to green. The resolution is good.

Thanks in advance.

---

