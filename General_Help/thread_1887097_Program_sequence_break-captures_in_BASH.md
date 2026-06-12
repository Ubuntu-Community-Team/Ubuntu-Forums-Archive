---
title: "Program sequence break-captures in BASH"
date: 2011-11-26
forum: General Help
---

### Post by chooyanzou on 2011-11-26
Are there any alternatives to ">" as in redirecting output to a file?

I'm running a program in my terminal wich generates a continouosly updated text output, similar to the **top**-command. But when I abort the program I want to send the screen output to a file.  The problem is that when using '>' the program continouosly sends the screen output (appending) to the file (though appending piping is not chosen), creating one huge f...g file.  =/

I want to just capture the screen output as displayed when I break/abort the program sequence. After typing the skin of my poor fingertips, I found no solution but to kneel before the gurus once again. Is there any way to make it function?

(If I somehow wasn't clear enough, I'm talking about text captures now, not graphic screen caps)  :)

A simple example:
```
 top > textfile
```

I want to capture all text output when I quit **top**.

---

