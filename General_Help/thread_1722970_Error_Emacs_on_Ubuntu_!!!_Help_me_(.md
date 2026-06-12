---
title: "Error Emacs on Ubuntu !!! Help me :("
date: 2011-04-06
forum: General Help
---

### Post by minhhai3b on 2011-04-06
I'm using Emacs 23 on Ubuntu 10.04 .Error : " ** (emacs:2686): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed " on Teminal when using Emacs.Can you help???Thanks!

---

### Post by TeoBigusGeekus on 2011-04-06
Change your gtk theme from murrine to something else.

---

### Post by Telengard C64 on 2011-04-06
You may also find it helpful to know that you can run Emacs inside the terminal window by passing it the **-nw** option on the command line. That way it should not matter what your desktop theme is.

---

### Post by Dave_L on 2011-04-06
> **TeoBigusGeekus said:**
> Change your gtk theme from murrine to something else.

How do you do that? (I'm running Ubuntu 10.04.)

---

### Post by TeoBigusGeekus on 2011-04-06
Right click your desktop>Appearance settings>Themes tab, pick a different one.

---

### Post by Dave_L on 2011-04-06
I was using the default theme, "Ambiance".  Is "murrine" an internal name for that?

Changing to a different theme got rid of the error message.

Thanks.

---

### Post by TeoBigusGeekus on 2011-04-06
Murrine is a gtk engine that some themes use. Probably the ambiance theme uses it and it conflicts with emacs.

If you really like your theme and prefer to keep it, but don't want emacs crushing, you could create a shortcut for emacs to open it using another theme:
```
GTK2_RC_FILES=/pathtoyouralternativenoncrushingtheme/gtkrc emacs
```

---

