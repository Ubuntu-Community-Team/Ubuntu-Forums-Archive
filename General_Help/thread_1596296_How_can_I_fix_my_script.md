---
title: "How can I fix my script?"
date: 2010-10-14
forum: General Help
---

### Post by tacomodo on 2010-10-14
I'm trying my hand at making a script. Can someone tell me why this doesn't work if $STATE doesn't have a value?

if [ $STATE = 0 ]; then
  echo "Great"
else
  echo "oh no"
fi

I would think that if $STATE was 0 then it would print "Great" and that if $STATE was *anything* else/empty, it would go to else and print "oh no".

---

### Post by luvshines on 2010-10-14
Although I am no scripting expert but you can try this:
```
(( STATE == 0 ))
```

But if I am not wrong, this will give STATE a default value of 0 if it has not been defined at all as you say it can be empty.

Then you can do this:
```
[ "$STATE" = 0 ]
```

This now makes that a string comparison and if STATE is not defined, it is null

---

