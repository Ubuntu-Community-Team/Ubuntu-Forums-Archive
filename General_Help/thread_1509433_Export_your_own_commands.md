---
title: "Export your own commands"
date: 2010-06-14
forum: General Help
---

### Post by Klump on 2010-06-14
Hey, I've got a simple question for advanced users - how can I export my own commands in terminal, for example, I want
```
metacity --replace &
``` to be accessed via ```
compizoff
``` command. Couldn't find anything useful myself so I came here :)

Thanks in advance!

---

### Post by gmargo on 2010-06-14
You can create your own commands with shell scripts, shell functions, and shell aliases. You only need one but here is your example as all three:

As a shell script:
Create a file $HOME/bin/compizoff with the text:
```

#!/bin/sh
metacity --replace &

```Make the file executable with "chmod +x $HOME/bin/compizoff".


As a shell function:
Edit your $HOME/.bashrc and add the following text:
```

compizoff()
{
      metacity --replace &
}

```As a shell alias:
Edit your $HOME/.bashrc and add the following text:
```

alias compizoff='metacity --replace &'

```When you open a new terminal window (i.e. invoke a new shell) that "compizoff" command will be available.

---

### Post by gingivere0 on 2010-06-14
I prefer the last option, but after you add the command to your .bashrc, you need to log off and log back on before the command will start to work.

---

### Post by elliotn on 2010-06-14
Wow

---

### Post by geirha on 2010-06-14
I recommend the second one, the shell function. For almost every purpose, aliases are superseded by shell functions. After editing .bashrc, start a new terminal, or paste the function into your current shell to have it defined in your current shell. You do not need to log out and back in again.

---

### Post by Klump on 2010-06-14
Thank you all, learned quite a lot today :)

---

