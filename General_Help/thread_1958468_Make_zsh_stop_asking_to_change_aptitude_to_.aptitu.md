---
title: "Make zsh stop asking to change aptitude to .aptitude"
date: 2012-04-14
forum: General Help
---

### Post by zombifier25 on 2012-04-14
Hi ya all,
I'm having a tiny (but really annoying problem) with zsh. When I type in  aptitude it keeps asking me if I want to change it to .aptitude  instead. So is there anyway to make the stupid terminal stop asking me to do so?

---

### Post by sj1410 on 2012-04-14
make sure your ~/.aptitude is readable and writable

can u paste the exact error or a screenshot.

---

### Post by zombifier25 on 2012-04-14
Actually, not that kind of error ;)
```
zsh: correct 'aptitude' to '.aptitude' [nyae]?
```whenever I try to launch sudo aptitude from the terminal, and I have to press 'n' everytime to have it NOT auto-correcting 'aptitude' to '.aptitude'. Very annoying. It doesn't happen when I just run aptitude though (no sudo).

---

### Post by outreal on 2012-06-23
I have exactly the same "issue". Really annoying, and it can get worse. If you try to install subversion, for example, while already having a folder called .subversion, this is what you get:

```
sudo aptitude install subversion
zsh: correct 'aptitude' to '.aptitude' [nyae]? n
zsh: correct 'subversion' to '.subversion' [nyae]? 
```

Any clues on how to disable this would be really appreciated.

---

### Post by krismatth3 on 2012-06-23
In your .zshrc, 

alias aptitude = 'nocorrect aptitude'

---

### Post by outreal on 2012-06-24
Hi krismatth3,

First of all, thank you for the answer!

I tried adding that line to my .zshrc (and reloading it by creating a new console) but it didn't work. But I noticed a strange behavior, independently of my adding the alias to my .zshrc: if I type "aptitude show tree", for example, it works. If I type "**sudo** aptitude show tree" then zsh asks me if I want to correct 'aptitude' to '.aptitude'.

Hope it helps.

---

