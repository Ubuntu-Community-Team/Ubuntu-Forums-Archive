---
title: "Open a terminal window by right click in file browser"
date: 2010-04-03
forum: General Help
---

### Post by J_dillinger on 2010-04-03
I have been attempting to find out how knoppix, Sabayan GTK, and several other Linux installations allow me to right click inside a folder in file browser to open a terminal window at that location.

Just as a sidenote, it would be handy to know how to open the3 file browser from a terminal window as well


Thanks...

---

### Post by geirha on 2010-04-03
It's a plugin for nautilus. Install it with the package [nautilus-open-terminal](apt:nautilus-open-terminal)

Oh and for the other way around, just run ```
nautilus .
```

---

### Post by J_dillinger on 2010-04-03
Thanks, that worked to add nautilus-open-terminal, and I can open nautilus from the terminal now, but there doesn't seem to be a session available for nautilus to run as a super user.  It isn't really a problem though because I can do most manipulations of files as super-user from the CLI or midnight-commander anyway.  


This is why ubuntu rocks.  This forum is way more supportive than any of the other distros I run on my boxes....

):P  :mrgreen:

---

### Post by Primefalcon on 2010-04-03
for right clicking ability with anything else you can use nautilus scripts too

[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)

basically all you do is design a bash script like this....

```
#!/bin/bash
xargs gpg --symmetric "$@"
```

replacing it with whatever commands you want, make the file executable and drop it in ~/.gnome2/nautilus-scripts

if it's your first script you'll have to restart nautilus for the scripts to show, easily done by

```
killall -9 nautilus; nohup nautilus
```

then just close the terminal and when you right click you'll notice a new command called scripts with your scripts in there, very useful

---

### Post by oldos2er on 2010-04-03
> **J_dillinger said:**
> Thanks, that worked to add nautilus-open-terminal, and I can open nautilus from the terminal now, but there doesn't seem to be a session available for nautilus to run as a super user.

There's the package **nautilus-gksu**, which adds a right-click menu entry 'Open as administrator'.

---

### Post by dcstar on 2010-04-03
> **oldos2er said:**
> There's the package **nautilus-gksu**, which adds a right-click menu entry 'Open as administrator'.

Funny how you can find all these things if you spend 5 minutes looking through Synaptic, isn't it?

---

### Post by gadolinio on 2010-04-03
> **geirha said:**
> It's a plugin for nautilus. Install it with the package [nautilus-open-terminal]("apt:nautilus-open-terminal")



Very useful! Thanks!

---

