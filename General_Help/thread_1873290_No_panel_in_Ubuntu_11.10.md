---
title: "No panel in Ubuntu 11.10"
date: 2011-11-01
forum: General Help
---

### Post by infinitybot on 2011-11-01
Hello guys,

Today I booted up Ubuntu just to  see Unity loaded without any panel . I can still fire up the terminal to load firefox , I can still view my desktop but I have no launcher/panel in Unity
Output of unity --reset
```

vibhav@p5kpl-ubuntu:~$ unity --reset
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done

```

Any help would be appreciated :D

---

### Post by infinitybot on 2011-11-01
UPDATE : Just fired ccsm to see the Unity Plugin Disabled , Enabled it , Now everything works fine
:D

PS: I wonder how did it get Disable?:confused:

---

### Post by botchniaque on 2011-11-18
Thanks for the post - have been trying 3 days to figure out what's wrong!

---

### Post by impelus on 2011-11-19
I believe I am having the same issue, but I'm not as savvy as you. How do you launch Compiz from terminal once at desktop?

Ctrl+Alt+T (for terminal)
Then type "ccsm" and hit enter?

I'm booted back into windows, otherwise I would try.

---

### Post by the_blue_box on 2011-11-19
First you need to install ccsm (if you don't have it already). Open the terminal and type...
```
sudo apt-get install compizconfig-settings-manager
```

Then as you said type
```
ccsm
```
and hit enter

Find "Ubuntu Unity Plugin" and if it's disabled , enabled it.
Good luck :)

[COLOR="Navy"]BB[/COLOR]

---

