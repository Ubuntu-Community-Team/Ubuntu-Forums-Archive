---
title: "Bash script works from terminal but not as keyboard shortcut"
date: 2011-09-19
forum: General Help
---

### Post by themonkeh on 2011-09-19
My bash script runs perfectly from the terminal but when I bind it to a key in the keyboard shortcuts menu it doesnt do anything. I copied the bound command and entered it into the terminal and it worked so it cant be a typo.  
bash /home/matt/scripts/switch-workspace.sh 
```
  
#! /bin/sh
current=$(wmctrl -d | sed -n 's/^\([0-9]\+\) *\*.*/\1/p')
if [ -z "$current" ]; then
  echo 1>&2 "$0: Could not obtain workspace information!"
  exit 2
fi

if [ $current = 0 ]; then
    xdotool key ctrl+alt+Right
    else
    xdotool key ctrl+alt+Left
fi

```I think the problem may be that ctrl+alt+Right/Left activate other commands in the keyboard shortcut window, but still dont know if theres a workaround or why that would be a problem. Any help is greatly appreciated.

---

