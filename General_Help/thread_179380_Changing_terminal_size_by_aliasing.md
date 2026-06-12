---
title: "Changing terminal size by aliasing"
date: 2006-05-19
forum: General Help
---

### Post by glinsvad on 2006-05-19
I'm slowly getting fed up with having to resize every gnome-terminal to a decent size, so I was wondering: Is this considered an aliasing "no-no"?
```

alias gnome-terminal='gnome-terminal --geometry=180x50'

```

I mean, aliasing the function as itself would prove to be an infinite recursive loop in some programming languages... right? :-k

Conversely, how else can I change the default width and height of GNOME terminals?

---

### Post by Slim Odds on 2006-05-19
[QUOTE=glinsvad]I'm slowly getting fed up with having to resize every gnome-terminal to a decent size, so I was wondering: Is this considered an aliasing "no-no"?
```

alias gnome-terminal='gnome-terminal --geometry=180x50'

```

I mean, aliasing the function as itself would prove to be an infinite recursive loop in some programming languages... right? :-k

Conversely, how else can I change the default width and height of GNOME terminals?[/QUOTE]

Try this instead:
```
alias gnome-terminal='command gnome-terminal --geometry=180x50'
```

That will avoid the infinite loop

---

### Post by dngpng on 2006-05-29
I've just came across a not-so-well solution: "System>Preferences>Preferred Applications", On the "System" tab, select "custom" for the Terminal Emulator, change the "command" field to "gnome-terminal --geometry 100x50 --working-directory=%f". Done!

---

