---
title: "Vim: Inserting yanked line in the middle of sentence"
date: 2009-11-08
forum: General Help
---

### Post by geo909 on 2009-11-08
Hi all,

I'm trying to learn vim here, and I have a small problem.
Let's say I have this text file:
```


This is the sentence I want to yank.

And I want to paste it here --> Yes, there.


```

So what I want to do is to copy (yank) the sentence
*This is the sentence I want to yank.* and place it
immediately after the arrow.
So I go to this line and press yy to yank it. Vim also
yanks the newline character at the end (\n).

Now, if I place the cursor after the arrow and press *p*
then this is what I will get:

```
  
This is the sentence I want to yank.

And I want to paste it here --> Yes, there.
This is the sentence I want to yank.

```

Whereas I would of course like to get
```
  
This is the sentence I want to yank.

And I want to paste it here --> This is the sentence I want to yank.
Yes, there.

```

Isn't this behaviour kind of odd?!

So, is there a (quick) way to do what I want?

Many thanks in advance..

---

### Post by DaithiF on 2009-11-08
rather than yank the whole line (yy), you can yank from the start to the end (excluding the newline), so 0y$, then p (or P) will work closer to what you expect, ie insert within the line.  You don't get the newline at the end unfortunately.  

Its to do with vim's idea of *linewise* vs *characterwise* operations -- yy is a linewise operation.  :help linewise for more info.

---

### Post by geo909 on 2009-11-08
> **DaithiF said:**
> rather than yank the whole line (yy), you can yank from the start to the end (excluding the newline), so 0y$, then p (or P) will work closer to what you expect, ie insert within the line.  You don't get the newline at the end unfortunately.  

Its to do with vim's idea of *linewise* vs *characterwise* operations -- yy is a linewise operation.  :help linewise for more info.

Many thanks.

I see, it is a bit strange, but I guess it works once you get used to it. Now that I think about it, it is not less efficient than 
```
Home, Shift + end, Ctrl + C
```
that I would do in a regular editor.

---

