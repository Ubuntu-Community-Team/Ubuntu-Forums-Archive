---
title: "How to check via terminal if external monitor is connected?"
date: 2010-04-20
forum: General Help
---

### Post by drewsus on 2010-04-20
Hello all, 

Ive been wondering about an alternative method for checking to see if an external monitor is connected. 
Currently I am using:
```
#!/bin/bash

EXTERN=VGA1

if $(xrandr --prop |grep -q "$EXTERN connected");then
  echo -e "$(echo $EXTERN | tr -d [0-9]) is \e[1;32mconnected\e[0m"
else
  echo -e "$(echo $EXTERN | tr -d [0-9]) is \e[1;31mdisconnected\e[0m"
fi
```

This will test run the command "**xrandr -q**" and check for the output "VGA1 connected" and output that it is connected where $?=0 or disconnected where $?>=1.

In xrandr's man page has a few options that seem like they might work nicely:
[QUOTE=man xrandr]-q
    When  this  option is present, or when no configuration changes are requested, xrandr will display the current state of the system.

--dryrun
Performs all the actions specified except that no changes are made.

--nograb
Apply the modifications without grabbing the screen. It avoids  to  block  other  applications  during  the update but it might also cause some applications that detect screen resize to receive old values.[/QUOTE]

**BUT** whenever I run "xrandr" with ANY option it displays the desired output and ENABLES the external monitor if it is connected. So, it does not allow me to only check to see if a monitor is present.

This presents a problem with compiz. Since, with my gfx card, I can only output a max texture size of 2048x2048, whenever 'xrandr' is "queried" and an external monitor is present, compiz is disabled with the following output:
[QUOTE=terminal]compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager[/QUOTE]

So, what I am asking is, is there a way to ignore/over-ride compiz's texture size check, a different way to query xrandr, or is there a completely different method I can go about checking if an external monitor is connected?

Drew

---

### Post by P4man on 2010-04-20
Some tips here to bypass the 2048x2048 limitation:
[http://ubuntuforums.org/showthread.php?t=1115208](http://ubuntuforums.org/showthread.php?t=1115208)

From the linked bug report in that thread:
[https://edge.launchpad.net/~cavedon/+archive/ppa](https://edge.launchpad.net/~cavedon/+archive/ppa)

---

### Post by drewsus on 2010-04-20
> **P4man said:**
> Some tips here to bypass the 2048x2048 limitation:
[http://ubuntuforums.org/showthread.php?t=1115208](http://ubuntuforums.org/showthread.php?t=1115208)

From the linked bug report in that thread:
[https://edge.launchpad.net/~cavedon/+archive/ppa](https://edge.launchpad.net/~cavedon/+archive/ppa)

Yeah, I actually replied to that thread. The problem is that PPA is only up to date for up to Jaunty. Im using Lucid, but I dont think it would be wise for Karmic either. It provides mesa 7.4 while I am using 7.7 and I don't know how to install it properly from that ppa. 

Furthermore, in that thread it mentions a compiz wrapper. Where can I find this to modify it?

---

### Post by drewsus on 2010-04-20
it seems that **/usr/bin/compiz-wrapper** has been replaced with **/usr/bin/compiz-decorator**. 

however, both have the lines: 
```
if [ -z "$XDG_CONFIG_HOME" ]; then
test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
test -f $XDG_CONFIG_HOME/compiz/compiz-manager && . $XDG_CONFIG_HOME/compiz/compiz-manager
fi
```
and I have read to add: 
> SKIP_CHECKS="yes"
to **$HOME/.config/compiz/compiz-manager**. I have done so, and even restarted, but I still get the error "Exceeded max texture size" which is accompanied by compiz failing. 

Any help with this issue or an alternative solution for checking if an external monitor is connected?

---

