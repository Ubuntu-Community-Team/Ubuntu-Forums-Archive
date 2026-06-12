---
title: "What's going on with the bootup process?"
date: 2006-02-08
forum: General Help
---

### Post by Leiki on 2006-02-08
Everytime I boot up Ubuntu on my laptop and it reaches "Configuring network devices" it takes about 2-5 minutes until it goes to the next step. Also when it reaches that point, the screen changes and all of the loadup processes are in big white letters (and the image and status bar is gone).

On my computer, however, the bootup is fairly fast and it completely loads normally (with the image and status bar). Does anyone know why this is and how I can fix it?

---

### Post by hod139 on 2006-02-08
My guess is that when you start your laptop you do not have an ethernet cable plugged into the ethernet port on your laptop. The 2-5 minute wait is your laptop timing out trying to establish a network conection on an ethernet port with no wire connected. (Or it could be your wireless card timing out). The screen is changing (I think) to the non-spash screen start up allowing you to see any error messages that may be occuring.

One thing you can do is hit Ctrl-C to kill the networking step, and it will continue booting.

Edit:  I should also add that another option is to use initNG [http://www.ubuntuforums.org/showthread.php?t=80423&highlight=faster+startup](http://www.ubuntuforums.org/showthread.php?t=80423&highlight=faster+startup)

---

