---
title: "login screen change"
date: 2010-06-17
forum: General Help
---

### Post by chudder on 2010-06-17
So I've been researching and it appears that altering the login screen theme is very different than previous versions.  I've figure out how to change the login background but here is my problem.  

I had the ubuntu studio theme and then I was trying to change the plymouth, and finally figured that out but in the process of tinkering I lost the theme (the actual window appearance) of the login window to look like Ubuntu Studio.  How do I fix this?

Thanks

chudder

---

### Post by sisco311 on 2010-06-17
Log out. 

Press Ctrl+Alt+F1 to switch to a virtual console  & log in.

Run:
```
sudo DISPLAY=:0.0 -u gdm gnome-appearance-properties
```

Press Ctrl+Alt+F7 [noparse](or F8)[/noparse] to switch back to the GDM login screen and change the theme.

Close the theme manager and log in.

---

### Post by chudder on 2010-06-17
I should probably clarify, I have the ubuntu studio theme in the session just fine, it is the login windo, etc that doesn't show it.  I'm not near my computer to try your code but I will as soon as I can.  

I don't know if my description changes anything.

Thanks for your help.

---

### Post by chudder on 2010-06-18
I typed the code in a virtual console after logging out and it said it couldn't open display.  I wasn't able to capture the exact wording but that's about what it said.

---

### Post by sisco311 on 2010-06-18
> **chudder said:**
> I should probably clarify, I have the ubuntu studio theme in the session just fine, it is the login windo, etc that doesn't show it.  I'm not near my computer to try your code but I will as soon as I can.  

I don't know if my description changes anything.

Thanks for your help.

The new GDM now uses GTK2 themes.  The command opens the theme manager on the login screen from where you can choose a new theme for GDM.

> **chudder said:**
> I typed the code in a virtual console after logging out and it said it couldn't open display.  I wasn't able to capture the exact wording but that's about what it said.

Try DISPLAY=:1.0 or DISPLAY=:2.0:
```
[FONT=monospace]
[/FONT]sudo DISPLAY=:1.0 -u gdm gnome-appearance-properties 
```

---

### Post by chudder on 2010-06-18
> **sisco311 said:**
> The new GDM now uses GTK2 themes.  The command opens the theme manager on the login screen from where you can choose a new theme for GDM.



Try DISPLAY=:1.0 or DISPLAY=:2.0:
```
[FONT=monospace]
[/FONT]sudo DISPLAY=:1.0 -u gdm gnome-appearance-properties 
```

sorry, still the same error.  In the past, changing the gdm theme was pretty painless, any idea why they don't have an easy built-in utility, I tried synaptic too and there doesn't seem to be anything.

Thanks for your help

---

### Post by sisco311 on 2010-06-18
> **chudder said:**
> sorry, still the same error.  In the past, changing the gdm theme was pretty painless, any idea why they don't have an easy built-in utility, I tried synaptic too and there doesn't seem to be anything.

Thanks for your help

Log in and run the command from a terminal without setting the DISPLAY variable:
```
sudo -u gdm gnome-appearance-properties
```

---

### Post by chudder on 2010-06-18
> **sisco311 said:**
> Log in and run the command from a terminal without setting the DISPLAY variable:
```
sudo -u gdm gnome-appearance-properties
```

I ran that line through and a window comes up saying this:

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with DBus, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

I'm removing anything that might be a KDE settings manager, to see if that will do anything.  I checked in synaptic and it appears that "gnome" isn't installed for some odd reason, I tried installing it but it says it can't because it depends on  swfdecmozilla and it won't install it for some reason

---

### Post by sisco311 on 2010-06-18
Sorry. Try:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by chudder on 2010-06-18
> **sisco311 said:**
> Sorry. Try:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```

I typed that in and it brought the Appearance Preferences manager, but i've been able to get that up and running before.  It's just the gdm theme I want to change.

After, doing some research, it appears that the gdm manager has been removed from the last few versions of Ubuntu.

---

