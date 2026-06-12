---
title: "Terminal Closes Automatically Because of Changed Preferences"
date: 2010-07-26
forum: General Help
---

### Post by Ast_risk on 2010-07-26
Hello, I can't open my terminal anymore. I changed a preference under the Title and Command tab in the preferences of the GNOME terminal. I put a custom command instead of the normal shell, but after I closed I realized that under the "When Command Exits" menu, I chose "Close Terminal". This means that the terminal closes automatically as soon as the command is done. After I open, it finishes the command and closes. I was wondering whether there is some way to change the terminal preferences from somewhere else or reinstall the terminal, and I obviously can't use terminal commands.:sad: Thanks for any help.

---

### Post by Ast_risk on 2010-07-27
Bump. I really need to get the terminal back up and running. If you need more info, please ask.

---

### Post by lukeiamyourfather on 2010-07-27
I don't have the answer to your question, but I'm sure someone else will. As a workaround until you figure out how to fix it, just use a different terminal like xterm, Konsole, Terminator, Guake, etc.

---

### Post by Ast_risk on 2010-07-27
I tried using xterm, but apparently they use the same preferences, and it closes too. :( I'm sure there has to be a workaround for this.

---

### Post by nothingspecial on 2010-07-27
If I have understood you correctly,

Press Alt F2

type ```
gconf-editor
```

Navigate apps > gnome-terminal > profiles > default

Scroll down untill you find "use_custom_command"

And uncheck (tick) the box.

---

### Post by Ast_risk on 2010-07-27
Thank you so much nothingspecial. It worked!:D I'm marking this as solved now.

---

### Post by nothingspecial on 2010-07-27
No problem :D

---

