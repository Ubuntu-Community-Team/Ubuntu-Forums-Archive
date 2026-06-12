---
title: "SSH to a TTY?"
date: 2011-06-19
forum: General Help
---

### Post by Ranko Kohime on 2011-06-19
I'm wondering if it's possible to control a TTY on a remote machine via SSH.

I'm aware of ssh's -t option, but it doesn't seem to do what I want.

Basically, I'm thinking in terms of VNC-like operation, where the remote user and local user see the same thing, only instead of a GUI, they both see TTY1 (or 2, or etc).

Is that doable, or no?

---

### Post by christopher.wortman on 2011-06-19
[http://ubuntuforums.org/showthread.php?t=1028066](http://ubuntuforums.org/showthread.php?t=1028066)

lol what you want is VNC not SSH lol

---

### Post by nothingspecial on 2011-06-19
You can do that with screen

or even easier with byobu

launch byobu on remote computer, then ssh in from the other one and type ```
byobu
```

You'll both see the same thing and can both type etc

so lol, you don't need vnc ;)

---

### Post by Ranko Kohime on 2011-06-20
> **nothingspecial said:**
> You can do that with screen

or even easier with byobu

launch byobu on remote computer, then ssh in from the other one and type ```
byobu
```

You'll both see the same thing and can both type etc

so lol, you don't need vnc ;)
Thanks.  It's a little different than I was thinking, but it seems to work well.  :)

---

