---
title: "Ctrl-left-arrow and Ctrl-right-arrow do not work in terminal"
date: 2010-06-27
forum: General Help
---

### Post by DigitalisCZ on 2010-06-27
*Problem:*
I recently updated to Xubuntu 10.4. I struggle to have working some keyboard bindings in virtual terminal (the terminal you get after pressing Ctrl-Alt-F1 etc).
In xfce-terminal as well as in xterm it works fine.

I am especially interested in **Ctrl-Left(Right)-Arrow** I would expect this will jump one work backward (forward) on command line. The standard readline bindings (Alt-B, Alt-F) works as they should but I do not want to change my typing habits just because of this....

*Observations:*
1. the /etc/inputrc does include expected definitions
```
# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word

```

2. there is no .inputrc in my $HOME. The environment variable $INPUTRC is unset. I tried to create my own .inputrc but this did not solve problem. Variable $TERM="linux".

4. when I issue in terminal Ctrl-V and 'key press' I do get absolutely same keyseq output:
Ctrl-left-arrow: ^[[D, Left-arrow: ^[[D
Instead doing this in xterm it gives keyseq ^[[1;5D which correspond to the definition in inputrc.

*Conclusion:*
I suspect that Ctrl key modifier used together with arrows is not correctly transferred to terminal. 

However I have no idea where to look for the fix. Thank you for your suggestions!

---

### Post by itcotbtoemik on 2010-06-27
See

[http://invisible-island.net/ncurses/ncurses.faq.html#modified_keys](http://invisible-island.net/ncurses/ncurses.faq.html#modified_keys)

The fundamental problem is that VTE-based programs (Terminal for instance)
use a convention for the key-modifiers which is copied from a long-ago
deprecated convention in xterm.  (xterm can be told to do the older
flavor, but that opens up a different can of worms).

---

