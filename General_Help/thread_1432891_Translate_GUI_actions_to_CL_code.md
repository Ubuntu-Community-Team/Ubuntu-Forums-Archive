---
title: "Translate GUI actions to CL code?"
date: 2010-03-18
forum: General Help
---

### Post by StepBack on 2010-03-18
The main thing I want to know is: how to translate my GUI actions into command-line code. I want to know if there is a command that outputs all the commands being made by interaction with my GUI.
Say, for example that I type this command and then open a file, the terminal would then print: "gnome-open /{path to file}".

Does this exist?


(The reason I ask is because I need to know a command to open with a non-default program. I have downloaded MiniCopier, so I want to add a launcher for it to my panel, by figuring out the code to launch it, but the default app to open ".jar" files is archive manager, rather than Java, so "gnome-open" doesn't do the trick. I've even changed the default to Java and still "gnome-open" uses archive manager, while double-clicking will use the new default=java. Weird...)

---

### Post by slakkie on 2010-03-18
Don't think it is really possible. Most GUI's would use the same libraries as the command line utils. Some apps, eg, k3b do use command line tools and you can view the details.

[k3b screenshot](http://opperschaap.net/~wesleys/2010-03-18-161056_1280x800_scrot.png)

---

### Post by StepBack on 2010-03-18
It's a shame that there's no way to do this. I got the idea from working with VBA in Microsoft Excel. You could do a "Record Macro" and then perform whatever actions you wanted and then click "Stop" and view the code that was behind all those actions. It made it very easy to learn the code.
Someone should make a similar feature for Ubuntu, it would help a lot of beginners learn Linux much quicker.


In any case, I found a way to solve the superficial issue: I realised the the .jar file I was opening wasn't the best to use, there was a ".sh" file in the folder too, and that one opens nicely with "gnome-open".

---

