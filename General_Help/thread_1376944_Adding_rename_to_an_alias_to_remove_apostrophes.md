---
title: "Adding rename to an alias to remove apostrophes"
date: 2010-01-09
forum: General Help
---

### Post by Arenlor on 2010-01-09
The line I currently have is:
[code]alias fixname="rename 's/[(),]//g' * && rename 's/ /_/g' *"[code]
I can't figure out how to add in so that it removes apostrophes too.

---

### Post by sisco311 on 2010-01-09
A non-quoted backslash (\) is the escape character.  It  preserves  the literal value of the next character that follows.

```
alias fixname="rename \"s/[(),**\'**]//g\" * && rename 's/ /_/g' *"
```

---

### Post by Arenlor on 2010-01-09
Thanks, that worked, just couldn't figure out the right combination of escapes.

---

### Post by sisco311 on 2010-01-09
> **Arenlor said:**
> Thanks, that worked, just couldn't figure out the right combination of escapes.

Yeh, it's tricky. 

It's much easier to write a bash function.

```
function fixname {
  rename ....
  rename ....
}
```

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-8.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-8.html")

---

