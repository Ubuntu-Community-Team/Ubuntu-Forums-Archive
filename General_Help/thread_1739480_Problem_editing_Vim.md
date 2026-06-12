---
title: "Problem editing Vim"
date: 2011-04-26
forum: General Help
---

### Post by MeKino on 2011-04-26
Hi,
I'm trying to edit a an html file with Vim and cannot find a way to prevent
the substitute command from continuing past where I want it to stop.
For example, the text is:
<span class=font10 style=" line-height:11.04pt; letter-spacing:0.40pt;">The
manager looked around him, saw nothing, then <span style="
letter-spacing:0.35pt;">glanced at his watch. The Saudi Ministers
were due back </span><span style=" letter-spacing:0.00pt;">in a few
minutes. There was time for him to make a routine </span><span style="
letter-spacing:-0.45pt;">check.</span></span></div>
I want to remove all the <span...> elements but the Vim command:
%s/<span .*">/ /gec
does not select them in the way I want.
Can anybody help?
Thanks

---

### Post by sweetleaf on 2011-04-28
.* is greedy.

Instead of .* (any number of any character),

```
%s/<span [COLOR="Red"].*"[/COLOR]>/ /gec
```

try using [^>]* (any number of any character except for >):

```
%s/<span [COLOR="Red"][^>]*[/COLOR]>/ /gec
```

To catch the closing tags at the same time, add \/\=:

```
%s/<[COLOR="Red"]\/\=[/COLOR]span [^>]*>/ /gec
```

---

### Post by MeKino on 2011-04-29
Thanks sweetleaf - you're a star!

---

