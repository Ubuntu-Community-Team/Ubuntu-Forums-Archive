---
title: "Can't Login as my User?"
date: 2011-05-30
forum: General Help
---

### Post by xandr55 on 2011-05-30
After a hard restart (xubuntu 11.4) I found that when attempting to login at the standard splash, it would flash vterm7 (the logs from boot, with some new stuff added, none of which looks unusual) and kick me back out to the login screen. I can login on a vterm and in a recovery console, but not into xfce session or xubuntu session. 

I have tried removing ~/.cache/xfce4 and ~/.config/xfce4 along with ~/.cache/sessions. 

I made a new user and can login to xubuntu under their name. 

Restarting gdm, or doing service gdm stop and startx don't work. 

Any ideas would be greatly appreciated. I really need this machine to do work on.

---

### Post by xandr55 on 2011-05-30
Ok so there is a workaround in case any one is experiencing this. I was worried that this would be the case. Maybe there is a better way but I couldn't figure it out and I really need to use this computer to get work done. Whatever failed failed horribly and ungracefully. 

Anyways this is what I did to get things up and running, though it isn't pretty:
```

ctrl-alt-f2 (logged into vterm)
mkdir dotfilesbk
mv .?* dotfilesbk/

```

If there were any errors I sudo mv'd them one by one. Once I had no .files except the obvious . and .., I logged in successfully. Once logged in I moved all the dotfiles that I KNEW weren't a problem .mozilla, .cabal, .bash_aliases, .bashrc etc. back, logged out and back in again, and most things work. I will go through one by one on the remaining folders to see where the problem is and post an update once I know in a couple of days. 

Not the end of the world but quite the PITA.

---

### Post by aeonofdiscord on 2011-12-27
Just had this same problem; looks like an xfce issue. I sorted it by removing everything under ~/.config/xfce4. My desktop settings got trashed, but I can log in again.

I'll poke around a bit and see if I can figure out which files were behind it.

(edit) ah. Turns out I messed up my .xinitrc trying to do something novel.

---

### Post by midden on 2012-03-08
I just ran into this same problem (Xubuntu 11.10). I logged in via a terminal (as you suggested) and then checked the ~/.xsession-errors file. It turns out that the system could not open my ~/.ICEauthority file, and indeed, that file was zero bytes. 

I deleted ~/.ICEauthority and was able to log in as usual.

---

### Post by Haz0 on 2012-03-23
> **midden said:**
> I just ran into this same problem (Xubuntu 11.10). I logged in via a terminal (as you suggested) and then checked the ~/.xsession-errors file. It turns out that the system could not open my ~/.ICEauthority file, and indeed, that file was zero bytes. 

I deleted ~/.ICEauthority and was able to log in as usual.

After reading about, this solution worked for me. My computer halted during the shutdown process without energy left, I could not log back into my user session without it knocking me back out into the log in screen before getting to the desktop.

For the layman, the command sequence I used (make sure to type commands with proper capitalization):

[LIST=1]
[*]CTRL + ALT + F1 from a guest user session. Enter credentials.
[*]Type this command: sudo rm -r ~/.ICEauthority
[*]End your current session, log back in as user
[/LIST]
Thanks for the tip and good luck to all! :biggrin:

---

