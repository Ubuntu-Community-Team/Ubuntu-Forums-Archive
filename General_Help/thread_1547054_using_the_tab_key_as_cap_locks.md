---
title: "using the tab key as cap locks ?"
date: 2010-08-06
forum: General Help
---

### Post by AlphaTheNeko on 2010-08-06
hi guys, new to the ubuntu forums and both the ubuntu/linux os in general. after my last topic that i got working, i realised i have the same problem as i did in windows, but cannot find a fix by google. and this is exactly why im not using capitals at the start of my sentences.

my cap locks key is broken and i want to use the tab key as my cap locks key. is this possible and how do i do it. i'm a linux noob :D

thanks in advanced for the help. - alphatheneko

---

### Post by Zorgoth on 2010-08-06
You could bind Tab to the command

"xdotool key Caps_Lock" if you have xdotool installed.

---

### Post by mali2297 on 2010-08-06
EDIT: New solution.

Create a file called .Xmodmap in your home folder. (Note the '.' in the filename, it means that it is a hidden file.) Put the following content in the file:
```

remove Lock = Caps_Lock
keysym Tab = Caps_Lock
keysym Caps_Lock = Tab
add Lock = Caps_Lock

```
In a terminal, run the command
```

xmodmap .Xmodmap

```
The keys for Tab and Caps Lock should now have been switched.

---

### Post by AlphaTheNeko on 2010-08-07
Excellent !! Thank you for the help !!! That worked as you can see :D Thanks so much guys !

---

### Post by sgosnell on 2010-08-07
Why can't you just use the Shift key for initial capitals?  That's why it's there.  I've never used the caps lock for intermittent capitals, just when I need a long string of capitals, and that's very seldom.

---

