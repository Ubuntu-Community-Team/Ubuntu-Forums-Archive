---
title: "Shell program argument tab-completion, how?"
date: 2011-01-30
forum: General Help
---

### Post by adcwoef on 2011-01-30
Hey!

For example:
```

$ find / -i <tab>
ilname iname  inum   ipath  iregex

```

So apparently you van get tab-completion not only for files but also for arguments to programs. How does this work? Is my shell communicating with the program and fetching a list of matching parameters? Does it guess by parsing the man file?

I'm curious to know. Thanks in advance.

---

### Post by AlphaLexman on 2011-01-30
```
locate bash_completion
```
will help you trace the script(s) to satisfy your curiosity.

---

### Post by Habitual on 2011-01-30
[http://bash.cyberciti.biz/bash-reference-manual/Shell-Expansions.html](http://bash.cyberciti.biz/bash-reference-manual/Shell-Expansions.html)

---

### Post by AlphaLexman on 2011-01-30
> **Habitual said:**
> [http://bash.cyberciti.biz/bash-reference-manual/Shell-Expansions.html](http://bash.cyberciti.biz/bash-reference-manual/Shell-Expansions.html)
Expansion and Completion are not the same thing!

---

