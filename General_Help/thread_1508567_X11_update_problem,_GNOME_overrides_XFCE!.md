---
title: "X11 update problem, GNOME overrides XFCE!"
date: 2010-06-13
forum: General Help
---

### Post by tinmice on 2010-06-13
Bit of a weird one this...

I used aptitude to update my 10.04 xubuntu system as normal, and didn't think anything of it. Carried on using it for a while before restarting without any problems. After restart it took ages to load and when it did the windows decorations etc were reset to standard and GNOME appears over the top of the XFCE, I think. 

I have a panel at the top of the screen in XFCE normally with all my stuff on, but now the GNOME panels at top and bottom appear over the top of it. The top behaves like it had autohide enabled but doesn't and it gets weirder still...

Using the guide on this site, [http://tech.akom.net/archives/46-Disabling-X-server-autostart-gdm-on-Ubuntu-Karmic-9.10.html](http://tech.akom.net/archives/46-Disabling-X-server-autostart-gdm-on-Ubuntu-Karmic-9.10.html) , I have disabled the autostart so I login in the shell and manually type startx. I thought that I might be able to select a session on login if i reenabled the gui login screen. When I did this I went to login with my username and password and it denied me entry. Same with root which is a bit worrying. In the end I had to use a rescue shell to disable the gui login again as in the above link. It then let me login in fine with the same username and password and manually type startx.

Really am confused and very annoyed. Any help or Ideas on how to go about fixing it would be hugely appreciated.

---

