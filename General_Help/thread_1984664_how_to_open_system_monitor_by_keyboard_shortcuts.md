---
title: "how to open system monitor by keyboard shortcuts?"
date: 2012-05-22
forum: General Help
---

### Post by Farhad16 on 2012-05-22
hi.
i understand that the system monitor is something like task manager at windows.
but i cannot open that by keyboard shortcuts.
i want to open that when i hold ctrl+alt+s
what is the comment i have to write at the keyboard shortcuts to make that open by hold those buttons?
thanks for any help
sorry if any mistakes, this isn't my native language

---

### Post by diesch on 2012-05-22
The command is
```
 gnome-system-monitor
```You can add one of the following options if you want it to open a specific tab:
```
 -s, --show-system-tab           Show the System tab
 -p, --show-processes-tab        Show the Processes tab
 -r, --show-resources-tab        Show the Resources tab
 -f, --show-file-systems-tab     Show the File Systems tab
```

---

### Post by prshah on 2012-05-22
> **Farhad16 said:**
> i want to open that when i hold ctrl+alt+s


Go to Dash (ubuntu icon)-System Settings-Keyboard-Shortcuts. The click the "+" icon (near the bottom) to add a new shortcut command. In the box that pops up (Custom shortcut), enter name as "System Monitor" and command as "/usr/bin/gnome-system-monitor". Click "Apply".

Now notice the shortcut key for this command is marked as disabled. Click on "disabled", the press the key combination you want for system monitor.

That's it, you can test it to check/change the keyboard shortcut.

---

### Post by Farhad16 on 2012-05-22
thanks a lot
both of the ways worked for me.;)

---

