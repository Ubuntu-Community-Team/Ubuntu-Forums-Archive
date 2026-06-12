---
title: "env command"
date: 2009-09-07
forum: General Help
---

### Post by metalmaniac248 on 2009-09-07
does the 'env' command (as in where you can set the environment something runs in like human or clearlooks) have to be run with root privileges? because i seems to have no effect unless prefixed with sudo,

---

### Post by Brandon Williams on 2009-09-07
I'm not sure what you're trying to do. The env command is used to override the posix environment (i.e. all of the NAME=VALUE pairs stored in your process's environment) when you run a command. It doesn't have anything directly to do with the theme (e.g. clearlooks or human) in use for an X windows application, except that there may be an environment variable that you can change to impact the theme used for a specific application.

So, are you saying that you want one app to use a different theme than the rest of your desktop? and that you're attempting to use an environment variable to indicate which theme should be used? If that's the case, what's the variable? and what does the command line you're using (without sudo) look like?

---

### Post by metalmaniac248 on 2009-09-14
this is the command i run (in this case to run skype with human)

```
sudo env GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc skype
```

 this works however i would like to not have to use root privileges to just to change the theme an app runs in

---

