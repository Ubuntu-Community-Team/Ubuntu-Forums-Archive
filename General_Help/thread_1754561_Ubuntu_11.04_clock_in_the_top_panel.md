---
title: "Ubuntu 11.04 clock in the top panel"
date: 2011-05-10
forum: General Help
---

### Post by kaefert66014235 on 2011-05-10
Has anybody run into problems with the clock of the top panel in Ubuntu 11.04? I can't open its settings (nothing opens when clicking on settings), and when I click on any date to view my calendar items of that date, the color of the text changes from white to black, and black text on dark gray background is NOT a good design choise..

Please tell me if you know a workaround or something. This problem seems to exist both in Unity and in the classic gnome desktop included in 11.04

EDIT: I just noticed the text color changes back to white (sometimes ;)) when he finished loading the calendar entries of that time..

But I still have the problem that I can't access the settings, which I need because I want to have the clock to show me seconds and also the date.

---

### Post by ubume2 on 2011-05-13
Are you using Unity or Ubuntu Classic?

This might not work. It may be too obvious

For Unity

Remove it and add it back.  Go to System Settings--Time and Date--Clock
Remove the checkmark from Show a Clock in the menu bar
Reboot
Go to System Settings--Time and Date--Clock & check the Show a clock in the menu bar
Reboot if necessary

---

### Post by kaefert66014235 on 2011-05-13
I found a solution to my problem here:
[http://ubuntuforums.org/showpost.php?p=10796126&postcount=35](http://ubuntuforums.org/showpost.php?p=10796126&postcount=35)

```
killall indicator-datetime-preferences
```

---

