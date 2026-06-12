---
title: "Can I change volume through command line?"
date: 2006-04-28
forum: General Help
---

### Post by TmP on 2006-04-28
Hi!

I need to find a command to change the volume of my cd audio capture, so that I put it into lirc.

And, btw. How can I put more commands into a desktop Louncher? Or does anyone know how to make short scripts to execute a few simple commands?

Yours trully.
Noob

---

### Post by kabus on 2006-04-28
[QUOTE=TmP]Hi!
I need to find a command to change the volume of my cd audio capture, so that I put it into lirc.
[/QUOTE]

Have a look at the amixer command.

[QUOTE=TmP]
Or does anyone know how to make short scripts to execute a few simple commands?
[/QUOTE]

Create a text file and enter this as the first line :
```

#!/bin/bash

```
Add your commands after that, save the file, and make it executable :

```
chmod u+x *yourfile*
```

for more information on shell scripting look here :

[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by TmP on 2006-04-28
Thanx!

My audio mixer is wierd, so instead of sending commands to it directly, I configured my LIRC to send commands to amixer.

Works fine.

---

