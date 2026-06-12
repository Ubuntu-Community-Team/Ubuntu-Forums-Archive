---
title: "Tip: Script to organize your favourite commands"
date: 2011-03-28
forum: General Help
---

### Post by nilseriksson on 2011-03-28
Hi,

I have written a command line script in ruby to organize and fetch your favourite commands.

See [https://github.com/nilseriksson/Mycommands](https://github.com/nilseriksson/Mycommands) for instructions.

Feel free to use it and come with ideas and comments.

Regards, Nils

---

### Post by nilseriksson on 2011-03-28
-

---

### Post by K.Mandla on 2011-03-31
Similar threads merged. Moved to General Help. :)

---

### Post by Habitual on 2011-03-31
```
history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
```

Output
```

127 sudo
91 ll
60 vi
58 devilspie
41 killall
33 cd
30 ping
27 search
22 bzr
21 install

```

Stolen from [Commandlinefu.com]("http://www.commandlinefu.com/commands/view/5845/list-of-commands-you-use-most-often")

---

### Post by nilseriksson on 2011-04-14
Here's an image that illustrates how it looks in action.

[IMG]http://img190.imageshack.us/img190/521/mycommands.png[/IMG]
[IMG]http://img190.imageshack.us/i/mycommands.png/[/IMG]

---

