---
title: "Sudo &amp; Question"
date: 2010-04-02
forum: General Help
---

### Post by pheebs on 2010-04-02
Doing some minor config file editing on my new system, so often my first terminal line I often type is:

```
sudo leafpad file &
```

Note it does not ask me to enter an admin password. I then see the process starting in the background.  When I 
```
ps -A
```
I see the PID listed not as leafpad, but as sudo just running in the background. My theory is that it gets sent to the background before it has a chance to query for the admin pass.
Is my assumption correct?
One workaround would be to sudo in the foreground and login, but I'm wondering if there's a better solution.
Thank you.

---

### Post by sisco311 on 2010-04-02
leafpad is a GUI text editor. For GUI apps you should use gksu. Since gksu is a GUI app you can start it in the background:
```
gksu leafpad file&
```


In general, you can stop an application with Ctrl+z, then send it to the background/foreground with the *bg/fg* command.

---

### Post by CompyTheInsane on 2010-04-02
Another way would be to run
```

sudo leafpad file

```
To be able to to sudo in the forground.
Then, pause 'leafpad file' by pressing ^Z (CTRL+Z)
and then run
```

bg

```
to resume leafpad in the background
EDIT: Replied too late. I like Sisco's reply better. Thank you. I never thought of using gksu in these cases.

EDIT 2: Using gksudo works as well.

---

### Post by pheebs on 2010-04-02
Ah, perfect, I forgot about gksudo.

Edit: note gksu, and gksudo did not come with the cli 9.10 install. An aptget on gksu seems to have fixed it!

Thank you for the extra info about bg/fg, never new that functionality existed.

---

