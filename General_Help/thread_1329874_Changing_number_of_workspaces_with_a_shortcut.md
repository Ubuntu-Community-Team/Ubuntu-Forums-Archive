---
title: "Changing number of workspaces with a shortcut"
date: 2009-11-17
forum: General Help
---

### Post by Noctiferis on 2009-11-17
Is there anyway I can use a keyboard shortcut to change the number of workspaces? Like super + j will add a workspace and super + k remove one.
I often work with lots of workspaces but I don't want to have more open than necessary when I'm just surfing. Any tips?

 Thank you 
 A Vagrant :D

PS Ubuntu 9.10 if it makes a difference

---

### Post by kaibob on 2009-11-17
I don't know of a quick-and-easy way to do what you want. Perhaps another forum member does.

If you are using metacity, the following shell script will change the number of workspaces. If the script name is changews, then the command to increase the number of workspaces would be "changews plus" (omit quotes) and the command to decrease the number of workspaces would be "changews minus".


```
#!/bin/bash

current=$(gconftool-2 --get /apps/metacity/general/num_workspaces)

if [ "$1" = plus ] ; then
   new=$((current + 1))
   gconftool-2 --type int --set /apps/metacity/general/num_workspaces $new
elif [ "$1" = minus ] ; then
   [ "$current" -eq 1 ] && exit 1
   new=$((current - 1))
   gconftool-2 --type int --set /apps/metacity/general/num_workspaces $new
fi
```

I tested this shell script and it works fine. Still, when messing with the gconf database, it's always good to have a solid backup.

---

### Post by Noctiferis on 2009-11-18
Uhm. I'm quite a noob here. I am using compiz. Is that what you mean by "If you are using metacity." Sorry fro my ignorance but on the comparison of x windows managers I found on wikipedia they are both listed so it means if I'm using compiz I am not using metacity?

---

### Post by kaibob on 2009-11-18
> **Noctiferis said:**
> Uhm. I'm quite a noob here. I am using compiz. 
The shell script won't work with compiz. I am not familiar with compiz, but it has many configuration options not available with metacity, so perhaps another forum member will be able to help.

---

### Post by Andreas1 on 2009-11-18
> **kaibob said:**
> The shell script won't work with compiz. I am not familiar with compiz, but it has many configuration options not available with metacity, so perhaps another forum member will be able to help.

the above script should work after replacing the metacity gconf keys with compiz ones. i don't have compiz installed currently, but i remember them being something like the following:

> /apps/compiz/...[something like horizontal virtual size]

run "gconf-editor" to find the exact keys and try them out

---

### Post by ububot on 2011-05-10
I wrote a script to do this. First, download wmctrl from the repositories. Then save the script below as ~/bin/chworkspaces or somewhere else you choose, make it executable, and then go into compiz settings and under "commands" add, e.g., "chworkspaces +" and "chworkspaces -". In a terminal type chworkspaces --help to see a full list of options.

```

#!/bin/bash

if [[ $1 == "-h" || $1 == "--help" ]]; then
    echo "USAGE: chworkspaces [ [hor|ver] +|- ] [ NxM ] [ -h|--help ]"
    echo ""
    echo "+ and - add or remove workspaces, respectively.  By default"
    echo "this adds one row and one column of workspaces. Using \"hor\""
    echo "specifies only to add a column; \"ver\" specifies only to add"
    echo "a row." 
    echo "Alternatively, \"NxM\" can be used as an input,  changing the"
    echo "grid of workspaces to NxM,  where N and M are both positive"
    echo "integers."
    echo "The -h or --help options show this message."
    exit
fi


SCREEN_SIZE=$(xrandr 2>/dev/null | grep "*" | grep -oP "\d+x\d+")
WIDTH=$(echo $SCREEN_SIZE | grep -oP "^\d+")
HEIGHT=$(echo $SCREEN_SIZE | grep -oP "\d+$")
CURRENT_SIZE=$(wmctrl -d | grep -oP "DG: \d+x\d+" | sed 's/DG: //')
CURRENT_WIDTH=$(echo $CURRENT_SIZE | grep -oP "^\d+")
CURRENT_HEIGHT=$(echo $CURRENT_SIZE | grep -oP "\d+$")
num_width=$((CURRENT_WIDTH / WIDTH))
num_height=$((CURRENT_HEIGHT / HEIGHT))

flag=$1
if [[ $flag =~ [0-9]+x[0-9]+ ]]; then
    num_width=$(echo $1 | grep -oP "^\d+")
    num_height=$(echo $1 | grep -oP "\d+$")
    wmctrl -g "$((num_width * WIDTH)),$((num_height * HEIGHT))"
    exit
fi

pm=-1
if [[ $2 == "+" || ($2 == "" && $flag == "+") ]]; then
    pm=1
fi
case $flag in
hor)
    wmctrl -g "$((WIDTH * (num_width + pm))),$CURRENT_HEIGHT"
    ;;
ver)
    wmctrl -g "$CURRENT_WIDTH,$((HEIGHT * (num_height + pm)))"
    ;;
*)
    wmctrl -g "$((WIDTH * (num_width + pm))),$((HEIGHT * (num_height + pm)))"
    ;;
esac

```

---

