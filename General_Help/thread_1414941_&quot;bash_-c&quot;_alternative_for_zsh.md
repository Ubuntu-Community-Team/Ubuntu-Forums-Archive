---
title: "&quot;bash -c&quot; alternative for zsh"
date: 2010-02-24
forum: General Help
---

### Post by Intrepid Ibex on 2010-02-24
So what is the "bash -c" alternative for zsh (the powerful bash)?

e.g. ```
konsole -e bash -c "bauerbill -Syu --aur"
```

```
konsole -e zsh -something "bauerbill -Syu --aur"
```

---

### Post by lloyd_b on 2010-02-24
It's been a while, but I *think* it's "zsh -t" to execute a single command, like bash's "-c" option.

Lloyd B.

---

### Post by gmargo on 2010-02-24
Is it so difficult to read the man page?  (Answer: Yes, the zsh man pages are a bit overwhelming.)

**-c** is the option you're looking for, just like bash. (The **-t** option reads a command from stdin.)

```

$ zsh --help | grep command
  -c         take first argument as a command to execute
  --singlecommand
  --onecmd                 equivalent to --singlecommand
  -t    equivalent to --singlecommand

```

---

### Post by Intrepid Ibex on 2010-02-24
Lol, it truly is -c. I just tried pacman without sudo which just prints the message that it should be performed as root - which made me believe it crashed instantly from wrong argument (even though it just printed the message and exited with status 0).

@gmargo, 'course it's difficult when you especially come to the forum to ask =P - that means I never even thought about the man pages. The man pages could be overwhelming to a Ubuntu user maybe.

---

