---
title: "No keyboard in xterm started by xinit in tty"
date: 2011-08-28
forum: General Help
---

### Post by Jarige on 2011-08-28
I'm trying to start an xserver by using this command in a tty (in this case, tty1):
```
sudo xinit -- :1
```
(didn't work without sudo)
This works, and it starts an xserver which I can see when pressing ALT-CTRL-F8. It starts an xterm by default, fine by me. The problem is, I can't type anything in that terminal. I can, however, change back to tty1 or the default Unity/GDM session on CTRL-ALT-F7. Keyboard works everywhere except for the started x session.

I would like to type in that terminal to SSH into my other computer and start a remote gnome-session. If there's a better way to do this, please tell me, keeping in mind that using SSH and xserver is preferred. I already have VNC set up and working, but that doesn't fit my needs (mainly because it doesn't adapt the resolution and it's slow).

Is there anyone who could tell me how to get my keyboard working in CTRL-ALT-F8?

In the hope that I've used the correct terminology for everything...

---

### Post by Jarige on 2011-08-28
This is /var/log/Xorg.1.log in which the attempt was logged:

[http://pastie.org/2444130]("http://pastie.org/2444130")

---

### Post by Jarige on 2011-08-28
Alright, I found out that I don't need to use 'sudo' for xinit. It starts with my own user too. Weird, I could have sworn that I couldn't run it as user at first. :???:

Is there anyone who could help me with this?

---

