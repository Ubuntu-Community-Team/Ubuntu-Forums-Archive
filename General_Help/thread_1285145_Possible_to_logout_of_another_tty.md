---
title: "Possible to logout of another tty?"
date: 2009-10-07
forum: General Help
---

### Post by rob86 on 2009-10-07
Let's say for some reason Ubuntu freezes up on tty7,  and luckily I can switch to another tty, is there any way to logout out of tty7 from another one ? For example a command like "logout tty7". Then I could jump to tty7 and start gdm..

I had some success just killing gdm and starting it again so maybe you can't log out of tty7 like that? It seems to be a special # and wouldn't let me use it without GDM running :)

Or even a more general question is, does anyone have any tips to recover from a computer freezing up. It often happens with some of the games I try, unfortunately. Sometimes it won't even let me switch to another tty to kill the process. One game I was playing (Privateer Gemini Gold) freezes up randomly and it takes about 5 minutes just to log in to tty1 and kill the process, because the CPU is being hogged, it's annoying!

---

### Post by Bachstelze on 2009-10-07
If you can't switch to a tty, you can SSH into yor computer from another one, and kill X from there.

---

### Post by wojox on 2009-10-07
You could try DontZap:

```
sudo apt-get install dontzap
```

Rebooot

Then Crtl+Alt+Backspace to kill X

---

