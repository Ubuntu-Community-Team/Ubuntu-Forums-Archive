---
title: "zsh: &quot;unalias -a&quot; = &quot;bad option: -a&quot;"
date: 2012-02-20
forum: General Help
---

### Post by Intrepid Ibex on 2012-02-20
Hey,

Whenever I do "**unalias -a**" with zsh it returns this:
```
&#9492;&#9484;(%:~)&#9484;- unalias -a
zsh: bad option: -a
```

I can get around it like this but I'd really prefer the former way:
```
unalias `alias | cut -d "=" -f1`
```

Ideas? I'm using the latest zsh (4.3.16).

---

### Post by Khayyam on 2012-02-20
Ibex ...

'unalias -a' is bash (and ksh, I believe), zsh only has the '-m' switch. The command requires a target/name, and the '-m' switch sets the target/name to be a pattern. Similarly with 'unhash -a' (which is the equiv of 'unalias').

So, to get the effect of bash's 'unalias -a' you should use 'unalias -m "*"'.

Note: the double quotes arround the glob are required.

HTH ... khay

---

### Post by Intrepid Ibex on 2012-02-20
khay ...

Yes. You're right.

ITD ... Ibex

---

