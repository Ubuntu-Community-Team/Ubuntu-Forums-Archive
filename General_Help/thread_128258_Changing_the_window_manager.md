---
title: "Changing the window manager"
date: 2006-02-11
forum: General Help
---

### Post by Ubuntuud on 2006-02-11
How do you change the window manager in gnome, I got openbox, fluxbox and sawfish, how do I use them? Thanks.

---

### Post by ebash on 2006-02-11
You can try setting the environment variable WINDOW_MANAGER 

Another option, although deprecated, consists of editing the gconf key /desktop/gnome/applications/window_manager/default. Try the following command:
gconf-editor /desktop/gnome/applications/window_manager

---

### Post by ebash on 2006-02-11
The following man pages can tell you more:
man gnome-wm
man gnome-session

Another alternative will be to create your own gnome-session script, take a look at man gnome-session. This could have some disadvantages because if the global session scripts change you will not see the new additions.

---

### Post by Ubuntuud on 2006-02-11
It says that I can edit default, but what should I edit, could you give a more detailed little howto? I'm still a noob you know...

---

### Post by ardchoille on 2006-02-11
Are you trying to log into another window manager instead of using the gnome desktop environment? Or do you want to use openbox instead of the Metacity window manager inside gnome?

If you want to use openbox as your window manager inside gnome, here's how I did it and it works great:

1) install a window manager (I installed openbox)

2) Put the following into ~/.gnomerc (create the file if it doesn't exist):
```

export WINDOW_MANAGER=/usr/bin/openbox

```

3) Open gconf-editor, go to apps/nautilus/preferences and uncheck "show_desktop" to make the openbox desktop menu appear, nautilus will continue to manage the desktop if this step is not completed.

Log out of gnome and back in and your new window manager should be managing windows for you.

If you use openbox, there is a nice menu editor called obmenu and can be found here: [http://obmenu.sourceforge.net/](http://obmenu.sourceforge.net/)

---

### Post by Ubuntuud on 2006-02-11
I wanted to used it inside gnome indeed an thanks alot, that's really useful.

---

### Post by ebash on 2006-02-11
Ok I did a little test on my computer and I managed to change the window manager. Here is what i did: edit the file ~/.profile, do the following: 
ALT-F2 (or start a shell) and enter the command:
gedit ~/.profile

Then in the text editor type
export WINDOW_MANAGER="afterstep"

You can replace afterstep by any other window manager like fluxbox or sawfish.
You will need to logout and login, but you can also try the settings by switching user.

Changing the window manager kind of works, both afterstep and fluxbox seen to try to replace GNOME. If you want to login into fluxbox or afterstep the best to choose that type of session in the login screen. 
Using sawfish works better as GNOME is left intact.

---

