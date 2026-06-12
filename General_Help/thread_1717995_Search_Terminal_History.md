---
title: "Search Terminal History"
date: 2011-03-30
forum: General Help
---

### Post by borgward on 2011-03-30
How do I search terminal command history? For example I want to search commands that start w/cp.

---

### Post by davidmohammed on 2011-03-30
this [link]("http://www.cyberciti.biz/faq/linux-unix-shell-history-search-command/") should give you some ideas.

---

### Post by seawolf167 on 2011-03-30
> **davidmohammed said:**
> this [link]("http://www.cyberciti.biz/faq/linux-unix-shell-history-search-command/") should give you some ideas.

+1

I came here to say to filter *history* through *grep*.

```
history | grep *command
```*

---

### Post by Krytarik on 2011-03-30
Also, you can use Ctrl+R to search the history while typing:
- press Ctrl+R again to get the next match
- press the left/right arrow keys to choose a found match, without immediately running it

Greetings.

---

