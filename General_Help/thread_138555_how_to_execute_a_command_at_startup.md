---
title: "how to execute a command at startup?"
date: 2006-03-02
forum: General Help
---

### Post by Jucato on 2006-03-02
Now it's my turn to ask. :D
I want to run the command "3ddesk --acquire" everytime I log in to my KDE session so that I could automatically get snapshots of my virtual desktops. How do I do this? I tried making a link in the ~/.kde/Autostart folder, but all it does is run 3ddesk, without the --acquire option. Maybe the fact that some SuperKaramba themes, Katapult, and KPager are also executed on startup affects it? How can I set it up so that 3ddesk loads last, after all the others have already run?

---

### Post by localzuk on 2006-03-02
try making a bash script such as

```

#!/bin/bash
3ddesk --aquire

```

and place it in the ~/.kde/Autostart directory with +x permissions.

---

### Post by Jucato on 2006-03-02
gee that was fast! :D
I was also thinking about scripts. But I'm an absolute newb when it comes to that. I'll try it out now. Thanks!

---

### Post by Jucato on 2006-03-02
It's a no go. I can run the script from the terminal, but it won't execute on startup. here's my script:
```
#! /bin/bash
exec /usr/bin/3ddesk --acquire
```

This time, it won't even execute 3ddesk. Will I be left to manuall --acquire everytime I startup... :(

EDIT: btw, I had to *sh script_name* to run it in the terminal, though.

---

### Post by metwo on 2006-03-02
[QUOTE=Fenyx]
EDIT: btw, I had to *sh script_name* to run it in the terminal, though.[/QUOTE]

have you set the permissions correctly (i.e. chmod +x script_name)?

---

### Post by Jucato on 2006-03-02
Yep. ls displays -rwxr-xr-x.
Oh boy... I'm such and idiot when it comes to scripts. :D

Btw, is there a way to execute this script execute after all the other items in my Autostart folder have loaded?

---

### Post by metwo on 2006-03-02
just to be clear, does it not run 3ddesk even if its executed from a terminal?

---

### Post by Jucato on 2006-03-02
it successfully run 3ddesk (with the --acquire option) when run from the terminal or when clicked from konqueror or when entered in the Run command.

---

### Post by localzuk on 2006-03-02
did you try the script I posted?

It may be the exec part? Hmm... I have never had a problem with executing an app directly as in my posted script.

---

### Post by Jucato on 2006-03-02
well maybe the problem is just with 3D Desktop. Oh well...
Thanks for your inputs! :D

---

### Post by dresnu on 2006-03-02
Have you checked the "is executable" box in the permissions tab of the file?

---

### Post by z-vet on 2006-03-02
I'm not completely sure, but in my opinion it have to be
```

#! /bin/bash
exec `/usr/bin/3ddesk --acquire`

```

---

### Post by Jucato on 2006-03-02
ok, I will try it once more... with the single quotes this time.
And yes, the script is executable (+x)
I also tried making a script for all the other startup programs that I have. It really seems that 3ddesk has a problem doing it's --acquire stuff during startup.

EDIT: nope, the single quotes (or double quotes even) don't work.

---

### Post by Jucato on 2006-03-02
AT LAST!! Finally! I got it to work! :D
So here's basically what I think happened.
3ddesk --acquire and the system notification sounds were somehow fighting with each other for priority. They can't be run together. So my solution was to do this little script:

```
#!/bin/bash
exec /usr/bin/3ddesk --acquire &
exec /usr/bin/superkaramba $HOME/Settings/SuperKaramba/cclock/cclock_shadow.theme &
exec /usr/bin/superkaramba $HOME/Settings/SuperKaramba/SuperMonitor5.4.skz &
exec /usr/bin/katapult &
exec /usr/bin/kompose & 
exec /usr/bin/kpager &
exec /usr/bin/kmix
```

Finally... I can rest in peace. :D
Thanks to everyone for your insights!! \\:D/

EDIT: Sorry for the double post. Accidentally pressed "Quote" instead of "Edit". :D

EDITED again: My jubilations were premature. It worked only once, or if System Notification Startup sound is disabled. Nevermind. I give up. :D

---

