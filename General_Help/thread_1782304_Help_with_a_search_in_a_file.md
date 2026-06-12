---
title: "Help with a search in a file"
date: 2011-06-14
forum: General Help
---

### Post by Sam White on 2011-06-14
Hi all,

I need to search a website source that I have downloaded for a URL which I only know part of. I know that it is in the format of "http://bit.ly" and then 6 characters.

I also need only the first instance, for there are multiple.

I have tried [COLOR=Red]grep -m 1 "http://bit.ly/......" *(insert file name here)*"[/COLOR], but this returns the whole line, and not just the string.

I have tried Googling, but strangely enough, no-one seems to want to search for a line and not have grep tell them where it is ;) :p

Any help is much appreciated.

Sam

---

### Post by Sam White on 2011-06-14
Bump?

---

### Post by nothingspecial on 2011-06-14
You are only supposed to bump every 24 hours

However, did you try the -o option?

---

### Post by Sam White on 2011-06-14
Sorry about that. 

Not at my laptop at the moment, but will give -o a try and will be sure to report back with my results.

---

### Post by nothingspecial on 2011-06-14
Reading your post again, I'm not 100% sure -o is what you want.

-o prints the exact match (not the whole line).

Is that what you wanted?

---

### Post by Sam White on 2011-06-15
Yes, -o is EXACTLY what I needed, thanks a lot!! You are a godsend!!

---

