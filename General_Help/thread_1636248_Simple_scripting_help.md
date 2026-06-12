---
title: "Simple scripting help"
date: 2010-12-02
forum: General Help
---

### Post by [E]vent[H]orizon on 2010-12-02
Hello! I am trying to make an executable script to run CS 1.6 with preferred settings. I don't want to have to type in this crap in the terminal every time I want to play so I'm trying to make this executable script... can someone tell me why this doesn't work?
```
$ cat > ~/bin/script
#!/bin/bash
# My first script
cd ~/.wine/drive_c/Valve/Steam/
wine Steam.exe -fullscreen -width 1024 -height 768 -applaunch 10 -heapsize 512000 & 
$ chmod +x !$
```Any help is appreciated!

---

### Post by Liverbones on 2010-12-02
Well... you don't have to pipe cat. You can just write [font="monospace"]cat ~/bin/script[/font]. But that's totally beside the point. :)

As for your script, as far as I can tell, it should work fine. But you need to make it executable by typing [font="monospace"]chmod +x script[/font], not [font="monospace"]chmod +x !$[/font], as all that's doing is echoing the file name back to your terminal (or whatever command you tried to execute last).

Hope that helps. :)

---

### Post by [E]vent[H]orizon on 2010-12-02
Ok I made the changes, but still no dice. Here's a bit more info:
The script file itself is on the Desktop (/home/connor/Desktop).
I just want it to run the cd and wine commands in the terminal.

---

