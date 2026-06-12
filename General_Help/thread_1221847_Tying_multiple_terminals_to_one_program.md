---
title: "Tying multiple terminals to one program?"
date: 2009-07-24
forum: General Help
---

### Post by dellwood on 2009-07-24
Hi, 

I was over at a co-workers cubicle who runs OS X.  His terminals acted as "one" program, for instance if he alt-tabbed to the single terminal process, it would show the 3-5 terminals he had open all at once.  Is this possible with gnome-terminal/another linux terminal?

Thanks :).

-Josh

---

### Post by kk0sse54 on 2009-07-24
I don't really know what you're looking for or anything about OS X for that matter but it sounds like you might want to look into something like [screen]("http://www.gnu.org/software/screen/"). Or perhaps you mean he was able to cycle through all is open terminal windows?

---

### Post by Whiffle on 2009-07-24
were they all displayed at teh same time or were they tabbed?

---

### Post by dellwood on 2009-07-24
Sorry if its hard to understand.  

Lets say I have terminal A and B.  They are separate terminals in separate frames and act as two separate terminals/frames EXCEPT if I alt-tab to them or select them on the window list they appear as one application, so if my window list looked like this:

```

_______________________________________________________________
Ubuntu Forums -Repl...| [zsh]           |Unsaved document 1-...
______________________|_________________|______________________

```  

(wrapped in code to preserve spaces)

...by selecting [zsh] it would show all opened terminals, and if I created a new terminal it would simply be tied to the set of terminals instead of receiving a new instance on the other side of "Unsaved document one."  I've used screen before, and am not sure it serves this functionality, because the "split" stays in one frame, though I may be wrong.

Hope that helps :).

-Josh

---

### Post by dlmarti on 2009-07-24
I think this is what your talking about, but its still not clear:
[http://www.terabytecode.com/stuff/explain.png](http://www.terabytecode.com/stuff/explain.png)

---

### Post by Whiffle on 2009-07-24
> **dellwood said:**
> Sorry if its hard to understand.  

Lets say I have terminal A and B.  They are separate terminals in separate frames and act as two separate terminals/frames EXCEPT if I alt-tab to them or select them on the window list they appear as one application, so if my window list looked like this:

```

_______________________________________________________________
Ubuntu Forums -Repl...| [zsh]           |Unsaved document 1-...
______________________|_________________|______________________

```  

(wrapped in code to preserve spaces)

...by selecting [zsh] it would show all opened terminals, and if I created a new terminal it would simply be tied to the set of terminals instead of receiving a new instance on the other side of "Unsaved document one."  I've used screen before, and am not sure it serves this functionality, because the "split" stays in one frame, though I may be wrong.

Hope that helps :).

-Josh



Oh I SEE. I never thought about till you asked, but you can do this with compiz (I just figured it out).  If you open compizconfig settings manager and then scroll all the way to the bottom, there is a plugin called Group and Tab Windows.  You can select windows to group together with Super+S, and then group them together with Super+G.

---

### Post by dellwood on 2009-07-24
That did the trick :).

Thanks.

-Josh

---

