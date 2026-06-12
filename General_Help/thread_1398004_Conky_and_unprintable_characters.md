---
title: "Conky and unprintable characters"
date: 2010-02-03
forum: General Help
---

### Post by TideMan on 2010-02-03
I've downloaded a .htm file from the WWW which has the following few lines:
> <h1>

Latest Times as at:  4-Feb-2010  15:30
${color3}${execi 1800 grep "Latest" FinishTimes.htm | sed -e 's/ in Tideda Files//'}

</h1>



and in my Conky script I do this:
```
${color3}${execi 1800 grep "Latest" FinishTimes.htm}

```

but when it prints on the screen there is an empty box at the end of the line.  
I assume this a CR or LF that's attached to the end of the line, but how can I get rid of it?

---

### Post by TideMan on 2010-02-04
Oh dear, this got screwed up.  It should have read:

> <h1>

Latest Times as at:  4-Feb-2010  17:30

</h1>


and
```
${color3}${execi 1800 grep "Latest" FinishTimes.htm}
```

---

