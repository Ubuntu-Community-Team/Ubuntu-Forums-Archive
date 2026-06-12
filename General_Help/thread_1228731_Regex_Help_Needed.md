---
title: "Regex Help Needed"
date: 2009-08-01
forum: General Help
---

### Post by Buce on 2009-08-01
I have a file with a these two lines:

```
  bwulf       user@blah.domain.stuff.edu:~/tmp
  bwulfuser@blah.domain.stuff.edu:~/tmp
```

I'm trying to match a regular expression to the first line, but not the second. Here's what I've got:

```
woody@bender:bin$ egrep "^\s*bwulf\s+($REG_EMAIL|$REG_IP)" /path/to/file.txt 
woody@bender:bin$ egrep "^\s*bwulf\s*($REG_EMAIL|$REG_IP)" /path/to/file.txt 
  bwulf         user@blah.domain.stuff.edu:~/tmp
  bwulfuser@blah.domain.stuff.edu:~/tmp
```

The first command misses both lines, and the second one catches both of them. What am I missing here?

---

### Post by unutbu on 2009-08-01
egrep (unlike perl) doesn't understand that \s means space. According to the man page, [[:space:]] is the egrep way to indicate the character class for whitespace. So
```

egrep "^[[:space:]]*bwulf[[:space:]]+($REG_EMAIL|$REG_IP)" /path/to/file.txt

```
seems to work for me.

---

### Post by Buce on 2009-08-01
```
woody@bender:bin$ egrep "^\s*bwulf +($REG_EMAIL|$REG_IP)" /path/to/file.txt
```

This seems to work, but only if the whitespace between 'bwulf' and 'user' is all spaces. I want it to work with both spaces *and* tabs. Isn't that what \s is supposed to do?

---

### Post by Buce on 2009-08-01
Oh, was typing while you posted. Thanks, unutbu!

---

