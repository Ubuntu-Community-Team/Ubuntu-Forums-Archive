---
title: "Removing certain lines from file in VI"
date: 2012-02-01
forum: General Help
---

### Post by agentguerry on 2012-02-01
Is there a easy way to remove certain lines with VI?

Example:

#
toast,eggs,bacon
,
,
bread,milk,
butter,
#

I want to leave any line in the file, OTHER than the lines with just "," on them.

I can't figure out how to do that, if I search for "," and remove, then it removes ALL the commas....

I was using :g/,/d

thank you.

---

### Post by bodhi.zazen on 2012-02-01
```
:g/^,$/d
```

See [http://www.softpanorama.org/Editors/Vimorama/vim_regular_expressions.shtml](http://www.softpanorama.org/Editors/Vimorama/vim_regular_expressions.shtml)

---

### Post by agentguerry on 2012-02-01
Oh sweet!

thanks a lot. this worked like a charm.
awesome when you have a csv file that is 9000+ lines.

:D

:popcorn:

---

