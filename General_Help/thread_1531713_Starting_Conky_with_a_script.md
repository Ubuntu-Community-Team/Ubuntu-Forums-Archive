---
title: "Starting Conky with a script"
date: 2010-07-15
forum: General Help
---

### Post by ferrospork on 2010-07-15
Hey, I've written 5 different Conkys, and I want them to all start when I log in, so I wrote a script shown below

#!/bin/bash
conky &
conky -c conkyrc_clock &
conky -c conky_processes &
conky -c conky_music &
conky -c conky_network


but it doesn't work. Can anyone show me where I've gone wrong?

conkyrc_clock, conky_processes etc are my different conkys.

thanks

---

### Post by stinkeye on 2010-07-15
> **ferrospork said:**
> Hey, I've written 5 different Conkys, and I want them to all start when I log in, so I wrote a script shown below

#!/bin/bash
conky &
conky -c conkyrc_clock &
conky -c conky_processes &
conky -c conky_music &
conky -c conky_network


but it doesn't work. Can anyone show me where I've gone wrong?

conkyrc_clock, conky_processes etc are my different conkys.

thanks

Use the full path to your conky config
Eg...```
conky -c /home/ferrospork/conkyrc_clock
```


It's also recommended if using gnome to add a delay into the script using the sleep commmamd
eg...```
#!/bin/bash
sleep 20 &&
conky &
conky -c [COLOR="Magenta"]conkyrc_clock[/COLOR] &
conky -c [COLOR="#ff00ff"]conky_processes[/COLOR] &
conky -c [COLOR="#ff00ff"]conky_music[/COLOR] &
conky -c [COLOR="#ff00ff"]conky_network[/COLOR]
```
[COLOR="#ff00ff"]Use the full path.[/COLOR]

---

