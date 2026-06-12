---
title: "Keyboard Shortcuts: Using PIPE for multiple commands"
date: 2010-08-28
forum: General Help
---

### Post by rocuan on 2010-08-28
Searched the forums for solution & am not seeing one
Wrote a simple script to find Trash folders on Lucid and delete them
```
#!/bin/bash
sudo find / -regex ".*Trash[-]?[0-9]+?" | while read -e line
do
    wipe -sfqr $line
done

```Added the script to a keyboard shortcut & it works dandy

I would like to pipe the script thru zenity for GUI feedback
```
/home/bin/dumptrash | zenity --progress --pulsate --auto-kill --auto-close --title "Dump Trash"

```works fine from command line
but is broken from Keyboard Shortcuts
Does the pipe symbol not work from Keyboard Shortcuts?

---

### Post by sisco311 on 2010-08-29
Try:
```
bash -c "/home/bin/dumptrash | zenity --progress ..."
```

---

