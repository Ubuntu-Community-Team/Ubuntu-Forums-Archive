---
title: "Followed a tutorial and messed some stuff up.."
date: 2011-03-30
forum: General Help
---

### Post by Insulted on 2011-03-30
I followed the tutorial here([http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25](http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25)), well, just ran the command in terminal then realized it was for an older version.

I prefer the desktop environment on Ubuntu Netbook Remix, which I can change while logging on, but whatever those lines did made it so that even when booting into the desktop mode, it still shows with the netbook layout/exactly as the netbook version does.

How do I reverse it?

Code:
```
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]xdg[COLOR=#000000]**/**[/COLOR]xdg-une[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]maximus-autostart.desktop [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]xdg[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]xdg[COLOR=#000000]**/**[/COLOR]xdg-une[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]netbook-launcher.desktop [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]xdg[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gconf[COLOR=#000000]**/**[/COLOR]une[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR][COLOR=#000000]20[/COLOR]_une-gconf-default [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gconf[COLOR=#000000]**/**[/COLOR]defaults[COLOR=#000000]**/**[/COLOR]
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**ln**[/COLOR] [COLOR=#660033]-s[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gconf[COLOR=#000000]**/**[/COLOR]une[COLOR=#000000]**/**[/COLOR]mandatory[COLOR=#000000]**/**[/COLOR][COLOR=#000000]20[/COLOR]_une-gconf-mandatory [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gconf[COLOR=#000000]**/**[/COLOR]defaults[COLOR=#000000]**/**[/COLOR]
[COLOR=#c20cb9]**sudo**[/COLOR] update-gconf-defaults
```

---

### Post by Insulted on 2011-03-30
Come on! I need help. D:

---

### Post by Insulted on 2011-03-31
Come on! I really really need someone to help. I was expecting quick help and all.

---

### Post by Rubi1200 on 2011-03-31
All you have to do is remove the symlink, same as any other file.

The only problem is I don't know whether or not you will also need to run the update command.

In the terminal:

```
sudo rm /etc/xdg/autostart/
sudo rm /etc/xdg/autostart/
sudo rm /usr/share/gconf/defaults/
sudo rm /usr/share/gconf/defaults/

``````
sudo update-gconf-defaults
```

Note: I haven't actually tried this, but it should work in theory.

---

### Post by n213978745 on 2011-03-31
> **Rubi1200 said:**
> All you have to do is remove the symlink, same as any other file.

The only problem is I don't know whether or not you will also need to run the update command.

In the terminal:

```
sudo rm /etc/xdg/autostart/
sudo rm /etc/xdg/autostart/
sudo rm /usr/share/gconf/defaults/
sudo rm /usr/share/gconf/defaults/

``````
sudo update-gconf-defaults
```Note: I haven't actually tried this, but it should work in theory.
I may be wrong, and I think the code should be:
```
sudo rm /etc/xdg/autostart/maximus-autostart.desktop
sudo rm /etc/xdg/autostart/netbook-launcher.desktop
sudo rm /usr/share/gconf/default/20_une-gconf-default
sudo rm /usr/share/gconf/default/20_une-gconf-mandatory
sudo update-gconf-defaults
```Since the /usr/share/gconf/default and /etc/xdg/autostart are both directories themselves.  And remember to make a backup for both directory before changing it, just in case if it doesn't work and become worse.

but before you are doing it, see if you can change it back to netbook edition by change the current seesion from gnome to others.


Also when I read the guide, it said:  If you want to customize the panel (or even delete/move it), the **only**  way is to switch to Gnome and use it as the default session.  You should read it more careful before making decision.

---

### Post by Rubi1200 on 2011-03-31
Sorry Insulted (my mistake), but n213978745 is absolutely right.

I wasn't paying attention to the syntax.

man ln explains it better.

And the other advice is also spot on.

---

### Post by Insulted on 2011-03-31
Well, I did what you said(2139798745), I used the following:
```

[COLOR=#c20cb9]**sudo**[/COLOR] rm [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]xdg[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]maximus-autostart.desktop
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR][COLOR=#660033][/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]xdg[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]netbook-launcher.desktop
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR][COLOR=#660033][/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gconf[COLOR=#000000]**/**[/COLOR]une[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR][COLOR=#000000]20[/COLOR]_une-gconf-default
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**rm**[/COLOR][COLOR=#660033][/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gconf[COLOR=#000000]**/**[/COLOR]une[COLOR=#000000]**/**[/COLOR]mandatory[COLOR=#000000]**/**[/COLOR][COLOR=#000000]20[/COLOR]_une-gconf-mandatory
[COLOR=#c20cb9]**sudo**[/COLOR] update-gconf-defaults
```

But the last to remove lines didn't get through, so I changed them.
Now I get the following error:
```
Traceback (most recent call last):
  File "/usr/bin/update-gconf-defaults", line 161, in <module> 
    read_entries(realname)
  File "/usr/bin/update-gconf-defaults", line 121, in read_entries
    for line in file(filename):
IOError: [Errno 2] No such file or diretory: '/usr/share/gconf/defaults/20_une-gconf-default'
```

I give up!
I'm just going to reinstall the OS. *sigh*

---

