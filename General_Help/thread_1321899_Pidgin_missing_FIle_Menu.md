---
title: "Pidgin missing FIle Menu"
date: 2009-11-10
forum: General Help
---

### Post by spyd4r on 2009-11-10
I am using Pidgin on Ubuntu 9.10 under openbox all other applications are fine, but Pidgin is missing its File Menu..

not really sure here, I have been forced to use keyboard shortcuts to change settings.

any suggestions on how to restore it?

---

### Post by hwttdz on 2009-11-10
Can you post the output of "pidgin -v; pidgin"

---

### Post by spyd4r on 2009-11-10
Pidgin 2.6.2 (libpurple 2.6.2)

btw, i also tried it under a gnome session, with and without compiz and its still missing...

---

### Post by mr_steve on 2009-11-10
> **spyd4r said:**
> Pidgin 2.6.2 (libpurple 2.6.2)

btw, i also tried it under a gnome session, with and without compiz and its still missing...

Do you by chance have the "Buddy List Options" plugin enabled? I notice that it has an option to hide the menu bar. Ctrl-U will bring up the plugins dialog to check.

---

### Post by spyd4r on 2009-11-10
> **mr_steve said:**
> Do you by chance have the "Buddy List Options" plugin enabled? I notice that it has an option to hide the menu bar. Ctrl-U will bring up the plugins dialog to check.

i dont see that plugin in my list actually.


i have the following enabled

extended preferences
libnotify popups
nautilus integration
pidgin gtk+ theme control
send button
timestamp
voice/video settings

---

### Post by mr_steve on 2009-11-10
> **spyd4r said:**
> i dont see that plugin in my list actually.


i have the following enabled

extended preferences
libnotify popups
nautilus integration
pidgin gtk+ theme control
send button
timestamp
voice/video settings

Odd. I don't actually have the extended preferences plugin installed, so I'm not sure if it has a similar option. I guess I'd start by disabling all the plugins and restarting Pidgin.

---

### Post by spyd4r on 2009-11-10
> **mr_steve said:**
> Odd. I don't actually have the extended preferences plugin installed, so I'm not sure if it has a similar option. I guess I'd start by disabling all the plugins and restarting Pidgin.

everything disabled.. 

no dice, still missing.. so odd.. :/

---

### Post by mr_steve on 2009-11-10
> **spyd4r said:**
> everything disabled.. 

no dice, still missing.. so odd.. :/

Well, about the last thing I can think of is to start Pidgin with a fresh configuration and see if it persists.

In your home directory, you'll have a hidden folder called .purple. With Pidgin closed, rename that folder to something else, like .pidgin.old, and start Pidgin again.

If the problem continues, you might have to remove and re-install Pidgin, or you might have some other issue with the window manager or something. Do any other applications exhibit this problem?

---

### Post by jdorenbush on 2012-04-27
First, shutdown Pidgin. Then, inside your **.purple** directory, open up **prefs.xml** in a text editor and search for this: 
```
<pref name='hidemenu' type='bool' value='1'/>.
```

If you find that, change the value from '1' to '0'. Save the file and restart Pidgin, and hopefully your menu will have been restored.

---

