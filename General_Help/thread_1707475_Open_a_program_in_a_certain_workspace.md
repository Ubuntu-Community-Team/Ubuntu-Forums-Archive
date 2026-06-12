---
title: "Open a program in a certain workspace?"
date: 2011-03-15
forum: General Help
---

### Post by pepsifx357 on 2011-03-15
What would be the terminal command, switch, or option to open a program in a  given workspace?

Say, I want to write a script that opens fire fox in the first workspace when the computer boots up.  Then, have open office writer in the second workspace followed by something else in the third, ect.?

---

### Post by wojox on 2011-03-15
There's a way to do it with compiz, but I personally don't know.

Look into devilspie it will do what you want for scripting.

---

### Post by TeoBigusGeekus on 2011-03-15
You could use wmctrl.
```
wmctrl -s 1 
firefox
wmctrl -s 2
openoffice-writer
wmctrl -s 3
thunderbird
....
```

---

### Post by pepsifx357 on 2011-03-15
The wmctrl thing didn't quite work, or at least I don't know enough about it to make it work.  It just jumped me to the next screen without opening the program.

---

### Post by wojox on 2011-03-15
[Devil's Pie documentation]("http://foosel.org/linux/devilspie")

[PHP]; Move firefox to workspace 2
(if 
  (is (application_name) "firefox-bin") 
  (set_workspace 2)
)[/PHP]

---

### Post by TeoBigusGeekus on 2011-03-15
Can you post what you did with wmctrl?

---

### Post by pepsifx357 on 2011-03-16
> **TeoBigusGeekus said:**
> Can you post what you did with wmctrl?

```
firefox wmctrl -s 2
```

That made the screen jump to the 3rd workspace and firefox did not open.

---

