---
title: "what does this \e[0;38;5;0m in .bashrc mean?"
date: 2010-02-22
forum: General Help
---

### Post by Uhuabin on 2010-02-22
I find a sample .bashrc for colored prompt in bash. normally we write some stuff like \e[0;30m to set colors. I know 0 means standard instead of bold. but don't understand why there is a 38 here. can't find that in the color chart. what does it mean? anybody help me pls? thanks.

---

### Post by gmargo on 2010-02-22
We were just talking about prompts over here: [http://ubuntuforums.org/showthread.php?t=1411222](http://ubuntuforums.org/showthread.php?t=1411222)

The control sequence document that comes with xterm (/usr/share/doc/xterm/ctlseqs.txt.gz) has this to say:
```

If 88- or 256-color support is compiled, the following apply.
  Ps = 3 8  ; 5  ; Ps -> Set foreground color to the second Ps
  Ps = 4 8  ; 5  ; Ps -> Set background color to the second Ps

```I think the sequence you gave is just setting the foreground color to black, twice.

---

### Post by Uhuabin on 2010-02-25
> **gmargo said:**
> We were just talking about prompts over here: [http://ubuntuforums.org/showthread.php?t=1411222](http://ubuntuforums.org/showthread.php?t=1411222)

The control sequence document that comes with xterm (/usr/share/doc/xterm/ctlseqs.txt.gz) has this to say:
```

If 88- or 256-color support is compiled, the following apply.
  Ps = 3 8  ; 5  ; Ps -> Set foreground color to the second Ps
  Ps = 4 8  ; 5  ; Ps -> Set background color to the second Ps

```I think the sequence you gave is just setting the foreground color to black, twice.

got it. it's setting foreground color. thank you very much :D

---

