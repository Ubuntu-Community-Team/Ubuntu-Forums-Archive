---
title: "Conky being clunky on startup"
date: 2011-01-04
forum: General Help
---

### Post by jvacek996 on 2011-01-04
I <3 Conky, and so I've set it up so it executes on startup.
The only thing is that at first, it is nicely blended with the desktop, but after other programs are executed it kinda hovers above other windows and even if the windows are in focus, the conky is still above, and the only way to get rid of this is to "killall conky" and then "conky"
is there a way to get rid of this or is it just my conkyrc (attached)?

thanks a lot!

---

### Post by stinkeye on 2011-01-04
Use a script to delay the start of conky until the desktop has loaded.
```
#!/bin/bash
#start Conky with a 20 second delay
sleep 20
[COLOR="Magenta"]conky[/COLOR] 

``` 

[COLOR="#ff00ff"]If your conky config is at **~/.conkyrc** leave as is.
If your config is somewhere else use **conky -c /path/to/your/config**[/COLOR]

Save the script with gedit as **start_conky** in your home folder.
Right click on file Properties > permissions and tick execute.

Open startup applications and edit your conky startup entry to point to the script
using the browse button.

---

### Post by jvacek996 on 2011-01-04
> **stinkeye said:**
> Use a script to delay the start of conky until the desktop has loaded.
```
#!/bin/bash
#start Conky with a 20 second delay
sleep 20
[COLOR="Magenta"]conky[/COLOR] 

``` 

[COLOR="#ff00ff"]If your conky config is at **~/.conkyrc** leave as is.
If your config is somewhere else use **conky -c /path/to/your/config**[/COLOR]

Save the script with gedit as **start_conky** in your home folder.
Right click on file Properties > permissions and tick execute.

Open startup applications and edit your conky startup entry to point to the script
using the browse button.

Great, seems it fixed it. But do you think the problem was on the developers side or in my .conkyrc itself? Just asking whether it's a bug in Conky or if it's me not thinking ahead :P

---

### Post by stinkeye on 2011-01-04
> **jvacek996 said:**
> Great, seems it fixed it. But do you think the problem was on the developers side or in my .conkyrc itself? Just asking whether it's a bug in Conky or if it's me not thinking ahead :P
Nah, it's just a commonly known problem with conky.

---

### Post by jvacek996 on 2011-01-04
K, Thanks a lot!

---

