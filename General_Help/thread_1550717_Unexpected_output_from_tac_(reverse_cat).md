---
title: "Unexpected output from tac (reverse cat)"
date: 2010-08-11
forum: General Help
---

### Post by Nephiel on 2010-08-11
I just ran into this while debugging a shell script. Narrowed the issue down to tac.

A simple test:
```
$ echo "alpha beta gamma delta epsilon" | tac -s' '
```
Expected result:
```
epsilon delta gamma beta alpha
$
```
Actual result:
```
epsilon
delta gamma beta alpha $
```

Another test:
```
$ echo -n "alpha beta gamma delta epsilon" | tac -s' '
```
Expected result:
```
epsilon delta gamma beta alpha$
```
Actual result:
```
epsilondelta gamma beta alpha $
```

Any idea why?

---

### Post by AlphaLexman on 2010-08-11
Put a space after epsilon ->
```
echo -n "alpha beta gamma delta epsilon " | tac -s' '
```

---

### Post by Nephiel on 2010-08-17
Thanks, that sort of works. But tac still puts the newline at the beginning rather than the end, though.

This is what I get:```
$ echo "alpha beta gamma delta epsilon " | tac -s' '

epsilon delta gamma beta alpha $
```
This is how it should be:```
$ echo "alpha beta gamma delta epsilon " | tac -s' '
epsilon delta gamma beta alpha
$
```

In my script I needed to reverse a list of words, separated by a space. tac didn't work well because of this - I ended up writing a few more lines of code to do it.

---

