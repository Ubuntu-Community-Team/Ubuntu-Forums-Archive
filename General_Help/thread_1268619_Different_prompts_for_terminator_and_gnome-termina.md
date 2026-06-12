---
title: "Different prompts for terminator and gnome-terminal"
date: 2009-09-17
forum: General Help
---

### Post by Renée Jade on 2009-09-17
Since I've started using Ubuntu I've used gnome-terminal for everything. I've got the prompt (as in the string before the '$' sign) showing date and time and stuff and I like it that way for everyday use. However, I've just been checking out terminator and I think it would be better for programming in (using vim + bash) because you can split it up instead of having to use tabs. But I don't want terminator to use the big fancy prompt. Does anyone know if there is a way to get terminator to display a different prompt to gnome-terminal? At the moment I've just written an alias that changes it but I would love if I could make it automatic with startup. Thanks. :)

---

### Post by Renée Jade on 2009-09-17
Ok, never mind. This works fine:

  alias p='PS1="\[\033[1;34m\]\w \$ \[\033[0m\]";clear'
  alias up='PS1="\[\033[1;34m\][\d \t] Renée: \w \$ \[\033[0m\]";clear'

added to .bash_aliases. I can deal with typing one letter :)

I never knew I could put more than one command in an alias. Semi-colon saves the day :D

---

