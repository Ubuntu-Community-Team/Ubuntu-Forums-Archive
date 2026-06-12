---
title: "compiz blur effect"
date: 2009-08-06
forum: General Help
---

### Post by charlie090790 on 2009-08-06
ok. i was messing with my compiz effects and once i turned on the blur effect everything slowy turned black. now everytime i log in everything turns black. i managed to log into a guest session blindly. i'd like to know if there is anyway i can disable the blur effect from the guest session, terminal or however so that i can use my account.

---

### Post by burmanabhay88 on 2009-08-06
try running this command in terminal and tell me if it works for u

*sudo gnome-appearance-properties %F*

---

### Post by issih on 2009-08-06
Drop to a proper terminal (ctrl+alt+F1)

Then log in (enter your username and password when prompted).

Now tell your gui session to use metacity as a window manager rather than compiz...

```
DISPLAY=:0.0 metacity --replace
```

Now return to your gui session (ctrl+alt+F7) and you should have a working gui again. Now go into CCSM and turn off the blur plugin.

You can now either log out and back in or hit alt+f2 to get a run dialog and enter:

```
compiz --replace
```

To turn the visual effects back on.

Hope that helps

---

### Post by NightwishFan on 2009-08-06
Reset the compiz settings in gconf, but I forget where they are stored... perhaps /apps/compiz??? I am not posting from Ubuntu so it is hard to remember.

HOWTO:

At login screen press alt+f5, you should see a commandline.
Log in as your user.
Run this command:

```
gconftool --recursive-unset /apps/compiz
```

---

### Post by charlie090790 on 2009-08-06
> **NightwishFan said:**
> Reset the compiz settings in gconf, but I forget where they are stored... perhaps /apps/compiz??? I am not posting from Ubuntu so it is hard to remember.

HOWTO:

At login screen press alt+f5, you should see a commandline.
Log in as your user.
Run this command:

```
gconftool --recursive-unset /apps/compiz
```

when run this command nothing happens?

---

### Post by charlie090790 on 2009-08-06
> **issih said:**
> Drop to a proper terminal (ctrl+alt+F1)

Then log in (enter your username and password when prompted).

Now tell your gui session to use metacity as a window manager rather than compiz...

```
DISPLAY=:0.0 metacity --replace
```Now return to your gui session (ctrl+alt+F7) and you should have a working gui again. Now go into CCSM and turn off the blur plugin.

You can now either log out and back in or hit alt+f2 to get a run dialog and enter:

```
compiz --replace
```To turn the visual effects back on.

Hope that helps
  when i run the display command . nothing happened. i went on and exited the gui and logged in and the same blackness happens D:

---

### Post by charlie090790 on 2009-08-06
whats the difference between running "gnome" instead of "last session" because i changed the session to "GNOME" and it runs fine without any compiz effects and the blur.

---

### Post by charlie090790 on 2009-08-06
uh.. i guess nvm thanks alot for trying to help :) i just changed the session to gnome, logged out and logged in into last session. it now works. i have no idea what exactly changing the session to gnome did. but it works :/

---

### Post by hibliss on 2009-08-06
It worked because it is no longer saving the settings from your last session.

---

### Post by charlie090790 on 2009-08-06
so what exactly does running the gnome session do?

---

