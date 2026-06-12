---
title: "Change prompt for current terminal only?"
date: 2011-02-07
forum: General Help
---

### Post by Pithikos on 2011-02-07
I program in C with geany and two terminals open; one to compile and one to test the compiled program.
The thing is that it's hard to the eyes to keep track of the messages and such when the terminal prompt is too long: ```
manos@manos-desktop:/media/Iomega1TB/Documents/UNI/Datastrukturer och Algoritmer/labbar/lab1$
```How can I change that to something minimal? I don't want a permanent solution as all other times I want to be aware of the current path.

---

### Post by nothingspecial on 2011-02-07
type

```
PS1=
```

Then you`ll have no prompt, but only for that terminal.

```
Or PS1=:
```

if you would like a :

To get your prompt back in that terminal without closing it, get it to read your .bashrc again

```
. ~/.bashrc
```

---

### Post by Pithikos on 2011-02-07
> **nothingspecial said:**
> type

```
PS1=
```Then you`ll have no prompt, but only for that terminal.

```
Or PS1=:
```if you would like a :

To get your prompt back in that terminal without closing it, get it to read your .bashrc again

```
. ~/.bashrc
```

Thanks!
I read about that when googling but got the idea that it was a global variable and thus would have an effect on all terminals. Thanks for the clarification. :p

---

### Post by nothingspecial on 2011-02-07
The variable is set in your .bashrc

you can have a lot of fun with it if you like that sort of thing.

---

