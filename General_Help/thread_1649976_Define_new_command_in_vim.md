---
title: "Define new :command in vim"
date: 2010-12-20
forum: General Help
---

### Post by Freelance Physicist on 2010-12-20
What I want to do is type the following vim colon command
```
:latexquotes
```
and have vim run the following two commands
```
:%s/"\</``/g
:%s/"/''/g
```

How do I define this command?

In case anyone is interested, these two commands replace straight quotes (") with latex-style quotes (`` '').

---

