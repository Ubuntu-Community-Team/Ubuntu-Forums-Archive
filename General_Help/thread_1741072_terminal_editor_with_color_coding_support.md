---
title: "terminal editor with color coding support"
date: 2011-04-27
forum: General Help
---

### Post by Mia_tech on 2011-04-27
guys, I'm doing some shell scripting in nano, but code is much simpler to read when is color coded.... is there a terminal editor that supports color coding?

thanks

---

### Post by 5149.5 on 2011-04-27
You can run Vim in a terminal or Gvim is GUI.

---

### Post by btindie on 2011-04-27
I think by default syntax highlighting should be enabled in nano.

The syntax files can be found in /usr/share/nano and the main configuration file for nano is in /etc/nanorc. See *man nanorc*.

You can force it to use a particular syntax highlighting file with
```
$ nano -Y sh <file>
```

'sh' is the syntax type defined in /usr/share/nano/sh.nanorc but if your shell script has the extension .sh or the correct header then you shouldn't need to force the syntax type.

---

### Post by Telengard C64 on 2011-04-27
You can start Emacs inside a terminal window by using the **-nw** option.

```
emacs -nw file_name
```

---

