---
title: "shutdown/reboot questions"
date: 2010-03-30
forum: General Help
---

### Post by blur xc on 2010-03-30
How come you can shut down or reboot from the gui w/o needing root privelages, but if I enter "shutdown -h now" on the command line I am met with "shutdown: Need to be root".

Also- somewhat unrelated to my first question- I recall when I first started Ubuntu-ing, if I wanted to shut down or reboot while another user was logged in, I'd need to enter my password- but it doesn't do that anymore.  Two users can be logged in with multiple applications open, and if I reboot or shutdown, it just goes for it?

(using 9.04, for now...)

Thanks,
BM

---

### Post by johngreth on 2010-03-30
There used to be a whole set of permissions settings for users that you could easily change. One of the options was about users needing to use a password to shut down. They did away with the permissions settings in 9.10, and the new setting is to not need a password. I don't know how to change it.

Also, I'm no expert, but I believe that the applet that has the session control buttons is automatically run with extra permissions.

Another possibility is that it already has permissions to edit the session because it is part of Gnome.

---

### Post by one-of-four on 2010-03-30
I believe that you can immediately shut down from terminal by using the "sudo shutdown -r now" command, I've used it before and it worked. Hope this helps!

---

