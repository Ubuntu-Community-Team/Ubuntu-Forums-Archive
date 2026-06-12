---
title: "BASH command line length?"
date: 2009-11-22
forum: General Help
---

### Post by Barriehie on 2009-11-22
Does bash have a limit to the cli line length???  I've got a cat to do on 137 absolute paths, which at this point comprises right about 5,4444 characters!

TIA,
Barrie

---

### Post by fluffman86 on 2009-11-22
It should work OK, but to make it more readable you can escape your new lines with backspace.  So:

```
scp /home/user/Documents/school/CSCI/CSCI251/Project1/code/c.out \
user@192.168.1.3:/home/user/Documents/school/CSCI/CSCI251/Project/code/c.out
```

is all read as a single line because the new line is ignored thanks to \

---

### Post by Barriehie on 2009-11-22
> **fluffman86 said:**
> It should work OK, but to make it more readable you can escape your new lines with backspace.  So:

```
scp /home/user/Documents/school/CSCI/CSCI251/Project1/code/c.out \
user@192.168.1.3:/home/user/Documents/school/CSCI/CSCI251/Project/code/c.out
```

is all read as a single line because the new line is ignored thanks to \

Thank you, I'll give that a shot here in a bit.  Worst case I can cat each file as it's processed.  Either way I'll post back!

Barrie

---

### Post by Barriehie on 2009-11-22
Well, I screwed up my emacs macro and ended up cat'ting each file as it was processed.  Good news is the script runs and now squid is blocking about 1.6 million sites.  Have to try the one liner after a nap :)

Barrie

---

