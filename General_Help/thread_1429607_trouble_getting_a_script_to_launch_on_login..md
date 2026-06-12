---
title: "trouble getting a script to launch on login."
date: 2010-03-14
forum: General Help
---

### Post by pixeldotz on 2010-03-14
hello everyone i've been looking for an answer to this for a few days now before i decided to post.

i have a simple script that works perfectly if launched manually from an xterm window.

the script has been already been chmod +x.

i have my account set to autologin to an xterm session.
i have symlinks in rc2.d and the script itself in init.d. i can't find any clear explanation of where i need to put my script to it launches itself right after my account logs into an xterm session.

i can ./script after my xterm session starts and everything works fine but i just cannot find where to put it so it launches after my acct auto logins.

fyi: i'm using xubuntu
anyone have any ideas?

---

### Post by gmargo on 2010-03-14
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

In general, files of the .desktop format residing in $HOME/.config/autostart will be started upon X session startup.  I know it works for gnome but have not tested xubuntu.

---

### Post by pixeldotz on 2010-03-14
it's not so much a desktop entry because i'm not auto logging into an xfce desktop.

my settings autolog me into an xterm session. so all i have is a nice pretty wallpaper and a white xterm window in the top-left of the screen.

i'm trying to get my bash script to launch at this point.

using runlevel tells me the xterm is @ runlevel 2 (N 2)

---

### Post by lswb on 2010-03-14
If it is an xterm login session, you could call your script from .profile.

OTOH if you are actually logging in to a regular desktop environment of some kind, most have a way of specifying startup applications. For instance, with gnome, Main Menu/System/Preferences/Startup Applications/Add.

---

### Post by pixeldotz on 2010-03-14
thanks for the help.

using your info i was able to track down that adding

./restore.pxl to the .bashrc file allowed it to run at login.

thanks again for all the help!

---

