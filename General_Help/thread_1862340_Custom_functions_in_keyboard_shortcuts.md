---
title: "Custom functions in keyboard shortcuts"
date: 2011-10-16
forum: General Help
---

### Post by Carborundum on 2011-10-16
I'm trying to create a keyboard shortcut to open the terminal; specifically, ctrl+alt+t, like in Vanilla Ubuntu. Mapping the command:
```
xfce4-terminal
```to said key combo works fine, except it opens a new terminal every time. If a terminal is already running, I want to  give it focus instead. Giving a window focus can be done with:
```
wmctrl -a _<WIN>_
```so I made this function to combine the two:
```
function terminal_keysc {
    if [ "$(pidof xfce4-terminal)" ];
        then
        wmctrl -a terminal;
        else
        xfce4-terminal;
    fi
}
```Problem is, mapping this function to a keyboard shortcut does precisely nothing. What I'm wondering is:

[LIST=1]
[*]Why doesn't it work?
[*]Is there some other way I can create context sensitive keyboard shortcuts?
[/LIST]
Thanks!

---

### Post by gsmanners on 2011-10-16
Save this into a file named "xfce-term.sh":

```
    if [ "$(pidof xfce4-terminal)" ];
        then
        wmctrl -a terminal;
        else
        xfce4-terminal;
    fi
```

Then:

```
chmod +x xfce-term.sh
```

Then select the script file in the "Command" column in the Keyboard setting application. Then press ctrl-alt-T to set your keyboard shortcut. And that should do it.

---

### Post by Carborundum on 2011-10-16
That did it! Thank you!

---

