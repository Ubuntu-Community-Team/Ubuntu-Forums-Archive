---
title: "Ubuntu 11.10 refuses to use themes"
date: 2011-11-23
forum: General Help
---

### Post by alquery on 2011-11-23
Title says it all: I can't use themes. The window borders change theme when I change the configuration options, but not the buttons, etc. I have tried all the tips I have found, I've removed config directories, and yet after I restart, it is still the same: I can't use a theme!

Related to this other thread of mine: [http://ubuntuforums.org/showthread.php?t=1871987]("http://ubuntuforums.org/showthread.php?t=1871987"). I thought I would start a new thread so people don't have to read through it to get to my current issue...

---

### Post by alquery on 2011-11-23
Screenshots didn't upload for some reason, here they are:

---

### Post by oldtimer7777 on 2011-11-23
> **alquery said:**
> Screenshots didn't upload for some reason, here they are:

Since Gnome 3 doesn't use GTK2 themes anymore, I was also having quite a bit of trouble trying to use the newer themes for Gnome 3 too. I don't know of a solution to get the themes working at this time.

---

### Post by carlbastos on 2011-11-23
Hey Al,

did you try moving the themes to /usr/share/themes and also checking they permissions? 

You can check [here]("http://askubuntu.com/questions/73576/appearance-does-not-change-on-switching-the-theme") too. Seems the same issue (caused by unity greeter).

If you think it's worth, I would do as they say, _backup my .config_ and delete it, to see if it solves the problem.

Regards,
Carl

---

### Post by alquery on 2011-11-24
> **carlbastos said:**
> Hey Al,

did you try moving the themes to /usr/share/themes and also checking they permissions? 

You can check [here]("http://askubuntu.com/questions/73576/appearance-does-not-change-on-switching-the-theme") too. Seems the same issue (caused by unity greeter).

If you think it's worth, I would do as they say, _backup my .config_ and delete it, to see if it solves the problem.

Regards,
Carl

Checking the permissions was one of the first things I did, but it seems that that's not the problem. I've also deleted all of my config files, but I'll try again. Hopefully just deleting .config/user/dconf will fix it.

It's definitely caused by running unity-greeter --test-mode, I did the exact same thing right before the problem started. Is there a bug report for this?

---

### Post by alquery on 2011-11-24
...and, due to some black magic, deleting the config again and logging out fixed it. Heh. Well, good to know that my UI wasn't permanently stuck in Windows 98 mode. Marking as solved, but somebody can post a link to a bug report if they find one.

---

### Post by alquery on 2011-11-24
I found the solution in [this (also solved) thread]("http://ubuntuforums.org/showthread.php?t=1861476") The dconf key that you need to change is: org.gnome.settings-daemon.plugins.xsettings.active.
Just check it and you should be good to go! I also answered the askubuntu question, hopefully it should be accepted in the near future.

---

