---
title: "Debug my Pipe Menu?"
date: 2010-01-24
forum: General Help
---

### Post by Saiko Berry on 2010-01-24
```
#!/bin/bash

$filepath ="/home/saiko/Root/Fuji/store_00010001/"

if [ "$1" = "--fujitoggle" ]; then
    if [ -d /home/saiko/Root/Fuji/store_00010001/ ]; then
        echo "Unmounting Camera"
    gksudo umount ~/Root/Fuji/
    else
        echo "Mounting Camera"
    gksudo gphotofs -o allow_other /home/saiko/Root/Fuji
        thunar ~/Root/Fuji/store_00010001/DCIM/100_FUJI
    fi
    exit 0
fi

# Output Openbox menu
if [ -d /home/saiko/Root/Fuji/store_00010001/ ]; then
    ACTION="Disable"
else
    ACTION="Enable"
fi

cat << _EOF_
    <openbox_pipe_menu>
        <item label="$ACTION">
            <action name="Execute">
                <execute>
                    ~/Root/FujiToggle --fujitoggle
                </execute>
            </action>
        </item>
    </openbox_pipe_menu>

_EOF_

exit 0
```

---

### Post by Saiko Berry on 2010-01-24
The problem is.. this line;
"    gksudo gphotofs -o allow_other /home/saiko/Root/Fuji"

It isnt running with gksudo or prompting me for a password or anything in order to mount the device.. Am I doing it wrong? Unmounting prompts me for a password just fine.

---

### Post by Saiko Berry on 2010-01-25
bump

---

