---
title: "How can I tell whether or not I'm in a terminal emulator?"
date: 2009-08-01
forum: General Help
---

### Post by Buce on 2009-08-01
Suppose that, in my .bashrc, I only want my fortune to appear when I pull up a terminal emulator (and not when I log into a text-only terminal without X running). How would I do this? What do I need in place of SOME_TEST in the snippet below?

```
[ SOME_TEST ] && fortune
```

---

### Post by Buce on 2009-08-01
I think I found the answer:

```
[ -z "$XAUTHORITY" ] || fortune
```

Confirmation that this is the right thing would be nice, though.

---

### Post by Buce on 2009-08-02
In case it should matter to anyone: when ssh'ing into a computer, $XAUTHORITY doesn't exist, so the snippet of code above will prevent fortune from being executed. It doesn't seem to matter whether or not you're forwarding X.

At least, that's the case for Scientific Linux.

---

