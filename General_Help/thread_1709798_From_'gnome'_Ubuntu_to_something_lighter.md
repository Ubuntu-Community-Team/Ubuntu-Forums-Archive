---
title: "From 'gnome' Ubuntu to something lighter"
date: 2011-03-18
forum: General Help
---

### Post by Toafan on 2011-03-18
I have an ancient laptop I decided is too old and incapable to run full Ubuntu. (Now, I'm sure this was a fine laptop back when it was new - in, like, '95. But we're talking like 3GB hard disk and ~256 MB ram - not up to today's standards). Since I don't have a replacement for it yet, I want to go to a pure 'light' interface - either lxde or xfce (unless someone recommends something else...).

However, I have files and stuff on here. I don't want to do a full clean install. And I don't know if I'll have enough space to install an entire environment and then go UN-install one. cleaning up to just GNOME may improve that, though.

I'm not afraid of the command line. (I may dislike the speed, but...) However, I do want access to a GUI - I'm not willing to live in a command-line, one-thing-at-a-time world. (now if it had tabs, a lá guake...)


UPDATE: since writing the above, I discovered the 'login to xterm' option on the login screen. Looking at Psychocats' tutorials, I'm assuming that this intended conversion would be a (relatively - very relatively) simple matter of logging in that way, uninstalling regular Ubuntu, and then installing lxde/xfce, eg:```

sudo apt-get remove adium-theme-ubuntu <massive snip>  whois xdg-user-dirs-gtk  xfonts-mathml && sudo apt-get install xubuntu-desktop   
```(except, of course, not that simple since I've already uninstalled stuff... among other things)
Anyone know better and willing to correct me?

---

