---
title: "XF86 Settings"
date: 2011-01-12
forum: General Help
---

### Post by decrow06 on 2011-01-12
Hello,

I am running 10.10 on a new Dell XPS 15.  The F1-F10 buttons on the keyboard are each labeled with a specific function.  For example, F2 toggles wireless on an off.  When I run the 'xev' command and press the F2 button, I am given keycode 246 corresponding to XF86WLAN.  However, I do not want my F2 button to toggle wireless because I would like it to work like a normal F2.  

When I run the command 
```

xmodmap -pke | grep -i f2

```

It tells me that keycode 68 corresponds to the F2 function.

My question is: how can I change the default XF86 settings that Ubuntu automatically detected?

Thanks.

---

### Post by rotave on 2011-01-13
You need to go into your system bios at startup. There should be an option for the function key behavior to be switched between multimedia or function. You need to set it to function for the F1-F12 keys to work as "normal" in Ubuntu.

---

### Post by decrow06 on 2011-01-13
Thanks a lot.

That worked well.  I have a few concerns.  I dual-boot with windows, and I would like my function keys to work as multimedia keys in windows.  Changing this setting in the bios changes the use in windows.  

Secondly, I like the multimedia keys, with the exception of F2, and possible F4.  What is my best option?

---

