---
title: "Help! Screen flashing on start up!"
date: 2010-08-29
forum: General Help
---

### Post by squidpotion on 2010-08-29
I tried to enable Compiz on my netbook, so I installed ccsm. Then when I enabled visual effects and restarted, my netbooks monitor starts flashing when I boot up. So I restarted in low graphics mode, uninstalled ccsm, and it's still flashing. Is there anything else I need to remove to get my netbooks monitor back to normal? Thanks!

---

### Post by quixote on 2010-08-30
The problem is probably that compiz still thinks it's enabled. You could start in recovery mode if the flashing makes the GUI version unusable. You'll need to login as you though, because the problem lies in your-user home directory settings. I'm showing the prompts in blue below, so it's clear who you're supposed to be as far as the system is concerned, but you don't type those in, of course. This is from memory, so I hope it's close enough so that it works!```
[COLOR="Blue"]root#[/COLOR] su - *your-user-name*
```(note the spaces on either side of the hyphen) This may ask you for your password again.  Not sure.```
[COLOR="Blue"]your-user$[/COLOR] metacity --replace 
``` ("compiz --replace" in a terminal would toggle it back to compiz again. You can also use "metacity --replace" in a terminal any time to toggle compiz off.)

---

