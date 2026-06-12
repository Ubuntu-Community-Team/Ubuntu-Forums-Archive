---
title: "Medal Of Honor Allied Assault (mohaa) - Mouse Scroll Wheel Not Functioning"
date: 2006-03-19
forum: General Help
---

### Post by Bradl3yJ on 2006-03-19
I have tried MOHAA using wine, i have tried it using cedega, the game installs and runs fine exept for the mouse wheel, I cannot change weapons with the mouse wheel. I try to configure the keys in the MOHAA options, and when it asks me to press the key i'd like to use, i scroll the mouse wheel up and it doesn't do a thing, it still waits for a key. In windows xp mouse wheel works fine in MOHAA. I have tested other the call of duty demo in cedega, and the mouse wheel works and can be binded. I have read the people have trouble with the mouse wheel using the native linux port, i havn't been able to get the linux port working, but i'd imagine its the same problem.

I have tried the workaround of using xkeybind and xvkbd, with this config file:

```
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Up]""
  m:0x0 + b:6
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Down]""
  m:0x0 + b:7
```

So when i scroll up, its like pressing the up arrow on the keyboard, and vis versa. This works in all applications, and infact it works when i run MOHAA in windowed mode through cedega, the mouse wheel sends up and down keypresses, but in fullscreen mode, it does not work. Does cedega run full screen games in a seperate environment causing xkeybind not to be in effect?

In any case, i am using a logitech usb mx500. I recall when i first got MOHAA on windows, certain logitech drivers did the same thing, mouse wheel would not function in mohaa. Is there a legacy way of sending the mouse wheel events that mohaa and some other older games require?


Does any one at all have MOHAA running with the ability to use the scroll wheel?

---

### Post by FkJ on 2007-05-01
Same problem here, any ideas?

---

