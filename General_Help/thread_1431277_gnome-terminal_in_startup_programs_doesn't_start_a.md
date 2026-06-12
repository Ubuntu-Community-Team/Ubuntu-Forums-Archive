---
title: "gnome-terminal in startup programs doesn't start at login"
date: 2010-03-16
forum: General Help
---

### Post by angry_norwegian on 2010-03-16
Every time I start Ubuntu, I set up an ssh session to a server. In order to automate this I made an entry in startup programs like this:

/usr/bin/gnome-terminal -e '/usr/bin/ssh [email]name@server.com[/email]'

Nothing happens when I log in, and I've checked that the command works.

What have I done wrong?

---

### Post by dcstar on 2010-03-17
> **angry_norwegian said:**
> Every time I start Ubuntu, I set up an ssh session to a server. In order to automate this I made an entry in startup programs like this:

/usr/bin/gnome-terminal -e '/usr/bin/ssh [email]name@server.com[/email]'

Nothing happens when I log in, and I've checked that the command works.

What have I done wrong?

Try putting that command in a script with a delay before it to allow the desktop to load before it is run.

---

### Post by prodigy_ on 2010-03-17
I use the following solution:

Make an addition profile (Edit/Profiles/New) for gnome-terminal, called SSH. In the "Title and Command" tab check "Run a custom command instead of my shell" and type your ssh command there with all options.

Then open System/Preferences/Startup Applications and make a new launcher. In the "Command" field type ```
gnome-terminal --window-with-profile SSH
```

---

