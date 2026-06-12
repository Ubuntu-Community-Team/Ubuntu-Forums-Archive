---
title: "Which kbmap am i using right now?"
date: 2011-02-24
forum: General Help
---

### Post by 3Nex on 2011-02-24
I want an output from the console to tell me which keyboard layout i'm using right now. Is there a command (or option for setkbmap that i couldn't find) that does that?

I want to implement the Alt-Shift equivalent from Windows that switches the keyboard layout to one of two, one being english and the other one my regional. To know which layout i'm using right now, i need to get a response of some sort as to which one is being used right now...

---

### Post by sisco311 on 2011-02-24
```
setxkbmap -print
```

For reference, here is the script I'm using:
```
#!/usr/bin/env bash

# List of languages:
LANGS=(us hu ro)

# List of variants:
VARIANTS=("altgr-intl" "qwerty" "")

# Path to the directory with the flag icons:
ICONPATH="/home/sisco/.icons/flags/png"
# You can download the icons from http://www.famfamfam.com/lab/icons/flags/
# The flag icon filenames must follow the ISO 3166-1 alpha-2 country codes.

# Set it to "true" to enable notification
# NOTE: you may have to install libnotify-bin
NOTIFY="true"
NOTIFYARGS="-h string:x-canonical-private-synchronous:true -h string:x-canonical-private-icon-only: \"notify\" "

CURRENT_LANG=$(setxkbmap -print | awk -F+ '/xkb_symbols/{print substr($2,1,2)}')

i=0
while [[ $CURRENT_LANG != ${LANGS[$i]} ]] && [[ $i < $((${#LANG[@]}-2)) ]];
do
  i=$((i+1))
done

if [[ $i = $((${#LANGS[@]}-1)) ]]; then
  NEWLANG=${LANGS[0]}
  NEWVARIANT=${VARIANTS[0]}
else
  NEWLANG=${LANGS[$((i+1))]}
  NEWVARIANT=${VARIANTS[$((i+1))]}
fi

setxkbmap "$NEWLANG" "$NEWVARIANT"

echo "$NEWLANG" "$NEWVARIANT"
if [[ $NOTIFY = "true" ]]; then
  notify-send -i "${ICONPATH}/${NEWLANG}.png" $NOTIFYARGS
fi

```

---

