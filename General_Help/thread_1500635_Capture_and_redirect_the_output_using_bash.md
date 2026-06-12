---
title: "Capture and redirect the output using bash"
date: 2010-06-03
forum: General Help
---

### Post by wvxvw on 2010-06-03
Hello.
Please excuse me if I'm posting to the wrong forum. Be so kind to tell me where to better ask this question, as I'm really not finding the right words to google for.

So, I have a shell application (fdb) which is a Flash debugger. 
I want to run it using bash script, capture it's output and pass it the commands (it can read from STDIN). The reason I want to do so is that Flash Builder (the IDE for Flash development) is plain stupid when it comes to compilation, and it won't allow me to compile any file in the project... so, I found out that I can make Eclipse to run an external tool. This external tool is my *.sh file which launches the compiler, and then it launches the debugger.
The Eclipse console then can display the compilation results, or errors. When I run the debugger it can even pass the input from Eclipse console to the debugger, however, the output from the debugger isn't shown.

Sorry for throwing at you all these details. Basically, what I need to know is how to make bash script as a shell for another application, that is, run it, get it's output, pass it the input.

TIA

---

### Post by zpletan on 2010-06-03
There are two ways to get output from program A to go to the input of program B.

If you want to keep the output for whatever reason, you can redirect it to a file:
```
programa > /path/to/file
program b < /path/to/file
```

If you just want the output to go to the input, use a pipe:
```
programa | programb
```

This will work from the command-line or a bash/sh script.  To make it a bash script, make a file with this:
```
#!/bin/bash
programa | programb
```
Then make sure it is executable by running:
```
chmod +x /path/to/bash/script
```

NOTE: Kinda obvious, but it's always good to make sure we're on the same page.  Replace programa with the program whose output you want, and replace programb with the program you want to feed input to.  Replace /any/paths/you/may/find with your own.

---

