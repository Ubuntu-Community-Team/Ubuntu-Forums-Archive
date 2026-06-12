---
title: "User looks in /usr/local/bin intead of /usr/bin"
date: 2009-12-19
forum: General Help
---

### Post by Skerit on 2009-12-19
I'm clearly overlooking something but have no idea what.

I've installed wine from git a while ago, but now I want to tryout 1.1.35.
So I rminstalled the git-wine and reinstalled wine 1.1.35.

When I run "wine" as root everything is going fine.
When I run "wine" as my regular user I get this error:

```
bash: /usr/local/bin/wine: Bestand of map bestaat niet
```
(File or directory doesn't exist)

So it's looking for /usr/local/bin/wine, even though wine is in /usr/bin ...

---

### Post by madverb on 2009-12-19
Is /usr/bin in your $PATH?

---

### Post by Skerit on 2009-12-19
Yes it is. I don't believe anything would work otherwise.

But the fact that he's saying that /usr/local/bin/wine doesn't exist is strange.
Any other, non-existing command gives a "command not found" error:

winel: command not found

---

