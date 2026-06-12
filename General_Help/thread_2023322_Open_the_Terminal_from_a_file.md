---
title: "Open the Terminal from a file"
date: 2012-07-12
forum: General Help
---

### Post by bramw on 2012-07-12
Hello all,
I was wondering if it is possible to start the Terminal (or command line interface) by opening just a file, like you would do in Windows by opening C:\Window\System 32\cmd.exe

---

### Post by MG&amp;TL on 2012-07-12
> **bramw said:**
> Hello all,
I was wondering if it is possible to start the Terminal (or command line interface) by opening just a file, like you would do in Windows by opening C:\Window\System 32\cmd.exe

What do you mean by 'opening'?

The terminal emulator for ubuntu is located at /usr/bin/gnome-terminal

---

### Post by modwyer8 on 2012-07-12
Hi-
Here is one way to launch the terminal from a file.  
You could make a file with the below text in there and save it to your bin folder:

```
#!/bin/bash
/usr/bin/gnome-terminal
```

Then change the permissions on that file with this command:

```
chmod +x {name of file}
```

You can then double-click on it and choose "Run" from the file browser.

If you had a terminal window open already you could run it using this command:

```
. {name of file}
```

Though an easy way to open a terminal window is with CTRL+ALT+T

---

