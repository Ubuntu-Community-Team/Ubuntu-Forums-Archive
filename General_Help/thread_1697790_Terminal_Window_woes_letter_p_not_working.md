---
title: "Terminal Window woes: letter p not working"
date: 2011-03-01
forum: General Help
---

### Post by kkruecke on 2011-03-01
As of this morning, whenever I open a terminal window, the letter 'p' no longer works. Uppercase 'P' works fine in a terminal window, but lowercase 'p' doesn't do a thing.  It isn't my keyboard, either (I can type 'p' here fine).

I tried checking the "Keyboard Shortcuts" (Edit->Keyboard Shortcuts..) for the terminal window, but 'p' is not assigned. 

Any ideas? This is bizarre. Any help would be greatly appreciated. I am running 10.10.

---

### Post by searchfgold6789 on 2011-03-01
Check to see if your keyboard layout is correct.

---

### Post by kkruecke on 2011-03-01
Thanks for your reply. How do I check if the keyboard layout is correct?
Here are some more details: It seems that lowercase  'p' is acting as Paste. Also when I set capslock on and then type p, I get this:

```
kurt@kurt-desktop:~$ keyboard layout is correct.
```

---

### Post by kkruecke on 2011-03-01
I'm not sure if 'p' is acting like Paste or like 'retrieve and execute previous command', that is, like the up arrow.

---

### Post by kkruecke on 2011-03-01
The keyboard layout (System->Preferences->Keyboard->Layouts tab->Show) is fine. So something else is overriding the keyboard layout for 'p', causing to act like Paste.

---

### Post by kkruecke on 2011-03-01
I reinstalled gnome-terminal and gnome-terminal-data. I thought this fixed it, but it didn't.

---

### Post by kkruecke on 2011-03-01
The keyboard shortcut key for the gnome terminal window got assigned to 'p' (somehow). Reassigning it to Ctl+V solved the problem.

---

