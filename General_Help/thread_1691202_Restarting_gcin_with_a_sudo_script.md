---
title: "Restarting gcin with a sudo script"
date: 2011-02-19
forum: General Help
---

### Post by kingtweety on 2011-02-19
I would like to run a sudo script on startup. Is it possible to run it without typing in a password? 

The script is simply "sudo killall gcin". This restarts the Chinese input method gcin. My understanding is that gcin has a bug, doesn't load properly upon startup, and only behaves correctly after a reset. 

Thus, I would like to have a script that executes the command "sudo killall gcin" upon startup without my typing in a password. Or even better, an easier workaround for gcin. 

Thanks for the help!

---

### Post by TeoBigusGeekus on 2011-02-19
[http://ubuntuforums.org/showthread.php?t=846470]("http://ubuntuforums.org/showthread.php?t=846470")

---

### Post by kingtweety on 2011-02-19
Thanks. I was hoping there would be a cleaner fix, since I am just trying to reverse a bug. 

I looked through the previous thread. I copied my script into /etc/init.d/ and executed update-rc.d <script> defaults. However, at the next login, the script doesn't load, and I need to kill gcin again. Did I do something incorrectly, or better yet, is there an easier fix so that gcin loads properly?

---

