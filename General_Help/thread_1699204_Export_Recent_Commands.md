---
title: "Export Recent Commands"
date: 2011-03-03
forum: General Help
---

### Post by john1923 on 2011-03-03
How do I export the last 10-15 commands that I typed into the command line?

I want to keep a record of what I have done in my lab book.

---

### Post by SeijiSensei on 2011-03-03
Use the "history" command.  If you want to save the history to a file, use something like

```
history > /home/user/myhistory.txt
```

or you can look at /home/user/.bash_history.  See "man history" for more details.

Histories can be long.  You can either edit a saved history, or pipe through "tail" to get the last N lines like this:

```
history | tail -n 20
```

would display the last twenty lines.

---

### Post by john1923 on 2011-03-03
Perfect. Thankyou

---

