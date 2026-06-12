---
title: "BASH Scripting Problem"
date: 2009-09-15
forum: General Help
---

### Post by abyrne on 2009-09-15
Hi,

   I'm having a small problem with a script I'm trying to write. I'm trying to redirect both stdout and stderr to both a log file and the user's screen. Right now I'm using:

```

#! /bin/bash
(
echo Hi
) | tee AKM.log
```

But that only redirects stdout to a file. How can I redirect both stdout and stderr to a file and a screen?

Any ideas?

---

### Post by unutbu on 2009-09-15
```
#!/bin/sh
(
echo Hi
) 2>&1 | tee AKM.log

```
See [http://bash-hackers.org/wiki/doku.php/syntax/redirection](http://bash-hackers.org/wiki/doku.php/syntax/redirection)

---

### Post by abyrne on 2009-09-16
Awesome! It worked! 
THANKS

---

