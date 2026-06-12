---
title: "Ubuntu booting, but can't log-in?"
date: 2012-03-11
forum: General Help
---

### Post by Spewed on 2012-03-11
Once again, I am facing a dilemma with Ubuntu, sorry guys. Originally  Gnome simply would not install on my machine. I did a fresh install of  Ubuntu 11.10, and that did the trick. I was able to install Gnome  afterwards. Since I got Gnome 3.2 I wasn't satisfied because I could not  use Compiz or Wobbly windows with it. I tried to fix that, and now I  cannot log into my Ubuntu 11.10. 

Here is what happens when I try to log in. I enter my password, and then  the screen turns black as if it's about to log-in but takes me directly  back to the log-in screen. The password IS being entered correctly, I  get no wrong password messages and I have double-even triple checked  just to make sure. 

It started doing that after I tried to make Compiz work with Gnome 3.2.  Here is what I did before the problem started. I created a folder called  "Gnomerc" in home folder, and then opened up my terminal and entered  this command. export WINDOW_MANAGER=/usr/bin/compiz

Since then I cannot log-in whatsoever. Is there a way to fix this  without YET AGAIN having to reinstall Ubuntu? :|. I tried to repair  broken packages but, it doesn't seem to actually do anything. So, is  there anything I can do from the live CD?

---

### Post by grahammechanical on 2012-03-11
Let us go over what has been done.

Ubuntu is based upon the gnome 3 desktop environment but as a default Ubuntu uses Unity as the User Interface and that uses Compiz as the window manager/compositing manager.

Gnome 3 shell is a different User Interface and it does not use Compiz. It uses some other compositing/window manager. You cannot use Compiz with Gnome shell.

When you installed Gnome shell you switched off Compiz. That has to happen in order for Gnome shell to run in Ubuntu.

Tell us what is that command supposed to do? What did you think that it would do? You have to put back what that command did. You may need to re-install Compiz. I guess that you need to re-start it as well.

In my opinion, a re-install is the easy option. It is not the clever answer but it usually fixes things.

Regards.

---

