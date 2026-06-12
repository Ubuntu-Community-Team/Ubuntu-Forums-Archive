---
title: "Unity bar not showing..."
date: 2011-10-24
forum: General Help
---

### Post by Chris Psycho on 2011-10-24
I was trying to disable the unity bar from autohiding.

So I went ahead and installed compiz config settings manager. However changing the 'setting' to 'never' didn't seem to be having any effect? Is there an apply button somewhere?

So anyway I went to the 'preferences' I think and hit reset and now my unity bar isn't showing at all... So I can't really open anything at the moment not even the terminal.

So please help guys :)

1. How do I get the bar back?
2. How do I disable it from hiding?

If I can't prevent it from hiding is there some easy way to switch applications? (A GUI) something like alt+tab.

It's a fresh install of ubuntu 11.10...

---

### Post by Chris Psycho on 2011-11-08
Bump?

---

### Post by Seb71 on 2011-11-08
Maybe you are using Unity 2D (compiz config settings manager does not work for this).

---

### Post by stinkeye on 2011-11-08
The unity plugin is disabled when you set compiz back to defaults using ccsm.
ie no panel or launcher.
Log out using ctrl+alt+del
or
ctrl+alt+SysRq(print)+k

At the login screen select your account, click on the cog icon, choose **ubuntu 2d** as the session and log on as normal.
Once logged on open
ccsm > preferences 
and reset to defaults.
Hit the back button and find and enable the Unity plugin.
You may as well set your **hide launcher** setting now also.

Log out and this time choose **Ubuntu** as your session at the log in screen.

---

### Post by Chris Psycho on 2011-11-08
Thank you so much :)

I get this though 'Some key and edge bindings of Plugin Ubuntu Unity Plugin conflict with other plugins. Do you want to resolve these conflicts?'

Clicking on resolve gives me messages like: The new value for the key binding for the action Key to execute a command in plugin Ubuntu Unity Plugin conflicts with the action Run Dialog of the Gnome Compatibility plugin.
Do you wish to disable Run Dialog in the Gnome Compatibility plugin?

What do I do now? :)

---

### Post by stinkeye on 2011-11-08
Click to disable.
Just click the far right button each time after choosing to resolve conflicts.

---

