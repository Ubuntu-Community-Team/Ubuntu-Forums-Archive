---
title: "targeting weird file names with autofil"
date: 2010-06-26
forum: General Help
---

### Post by mchlor on 2010-06-26
greetings,

In terminal,  How do I target file with name beginning with parenthesis?

```
(ex) example.jpg
```

I can't remove it coz I can't target it hehe.  I tried ```
(ex +tab
``````
`(ex + tab
``````
+space (ex +tab
```

I'm out of ideas.

I don't have X installed.

---

### Post by AlphaLexman on 2010-06-26
Put a backslash \ in front of each ( ).

---

### Post by Exp HP on 2010-06-26
Two ways.  You can quote it, or escape the strange characters with backslashes (\).
```
(ex)\ example.jpg
"(ex) example.jpg"
'(ex) example.jpg'
```Incidentally, for even weirder filenames (like ones with quotes or backslashes), you can do this:

"ex" example.jpg
```
'"ex" example.jpg'
\"ex\"\ example.jpg
```"ex" 'ex\ample'.jpg
```
"\"ex\" 'ex\\ample'.jpg"
\"ex\"\ \'ex\\ample\'.jpg
```

---

### Post by mchlor on 2010-06-26
thank you much, marking this thread solved.

---

